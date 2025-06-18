import re

def is_snake_case(name):
    return bool(re.fullmatch(r'[a-z]+(_[a-z0-9]+)*', name))

def is_camel_case(name):
    return bool(re.fullmatch(r'[a-z]+(?:[A-Z][a-z0-9]*)+', name))

def analyze_code(file_path):
    with open(file_path, 'r', encoding='utf-8') as f:
        lines = f.readlines()

    total_lines = len(lines)
    comment_lines = sum(1 for line in lines if line.strip().startswith('#'))

    generic_names = ['data', 'data_list', 'temp', 'input', 'output', 'process', 'result']
    generic_functions = ['main', 'process_data', 'check_input', 'handle_request']

    snake_case = 0
    camel_case = 0
    generic_name_hits = 0
    try_except_blocks = 0

    for line in lines:
        line = line.strip()

        # Count naming patterns
        function_match = re.findall(r'def (\w+)', line)
        variable_match = re.findall(r'(\w+)\s*=', line)

        for name in function_match + variable_match:
            if is_snake_case(name):
                snake_case += 1
            elif is_camel_case(name):
                camel_case += 1

            if name.lower() in generic_names or name.lower() in generic_functions:
                generic_name_hits += 1

        if line.startswith('except Exception') or 'Exception as' in line:
            try_except_blocks += 1

    # Heuristic scoring
    comment_ratio = comment_lines / total_lines if total_lines else 0
    naming_ratio = camel_case / (snake_case + camel_case + 1e-6)
    generic_ratio = generic_name_hits / total_lines
    try_ratio = try_except_blocks / total_lines

    # Simple weighted score
    ai_likelihood = 0
    if comment_ratio > 0.25:
        ai_likelihood += 1
    if naming_ratio > 0.2:
        ai_likelihood += 1
    if generic_ratio > 0.05:
        ai_likelihood += 1
    if try_ratio > 0.02:
        ai_likelihood += 1

    print(f"\n🔍 Analysis of {file_path}:")
    print(f" - Total lines: {total_lines}")
    print(f" - Comment ratio: {comment_ratio:.2f}")
    print(f" - CamelCase ratio: {naming_ratio:.2f}")
    print(f" - Generic name hits: {generic_name_hits}")
    print(f" - try/except blocks: {try_except_blocks}")

    print("\n🤖 AI-Likeness Score:", ai_likelihood, "/ 4")

    if ai_likelihood >= 3:
        print("🔸 Likely AI-generated or heavily AI-influenced.")
    elif ai_likelihood == 2:
        print("⚠️ Possibly AI-assisted code.")
    else:
        print("✅ Likely human-written code (or edited by human).")

if __name__ == "__main__":
    filepath = input("Enter path to Python file: ").strip()
    analyze_code(filepath)
