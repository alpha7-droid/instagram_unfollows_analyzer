# instagram_unfollows_analyzer

import os
import json

def find_file_anywhere(base_folder, target_filename):
    target_filename = target_filename.lower()

    for root, dirs, files in os.walk(base_folder):
        for f in files:
            if f.lower() == target_filename:
                return os.path.join(root, f)

    return None


def load_json_by_search(base_folder, filename):
    file_path = find_file_anywhere(base_folder, filename)

    if not file_path:
        print(f"❌ File not found: {filename}")
        print("👉 Tip: BASE_FOLDER galat hai ya file exist nahi karti.")
        return None

    print(f"✅ Found file: {file_path}")

    with open(file_path, "r", encoding="utf-8") as f:
        return json.load(f)



BASE_FOLDER = "D:\"

FILENAME = "recently_unfollowed_profiles.json"

data = load_json_by_search(BASE_FOLDER, FILENAME)

if data:
    print("✅ Loaded Successfully!")
    users = data.get("relationships_unfollowed_users", [])

    print(f"\n📌 Total Recently Unfollowed: {len(users)}\n")

    for i, u in enumerate(users[:20], start=1):
        try:
            info = u["string_list_data"][0]
            print(f"{i}. {info.get('value')}  ->  {info.get('href')}")
        except:
            print(f"{i}. (format error)")
import os
import json

def find_file_anywhere(base_folder, target_filename):
    target_filename = target_filename.lower()

    for root, dirs, files in os.walk(base_folder):
        for f in files:
            if f.lower() == target_filename:
                return os.path.join(root, f)

    return None


def load_json_by_search(base_folder, filename):
    file_path = find_file_anywhere(base_folder, filename)

    if not file_path:
        print(f"❌ File not found: {filename}")
        print("👉 Tip: BASE_FOLDER galat hai ya file exist nahi karti.")
        return None

    print(f"✅ Found file: {file_path}")

    with open(file_path, "r", encoding="utf-8") as f:
        return json.load(f)



BASE_FOLDER = "D:\"

FILENAME = "recently_unfollowed_profiles.json"

data = load_json_by_search(BASE_FOLDER, FILENAME)

if data:
    print("✅ Loaded Successfully!")
    users = data.get("relationships_unfollowed_users", [])

    print(f"\n📌 Total Recently Unfollowed: {len(users)}\n")

    for i, u in enumerate(users[:20], start=1):
        try:
            info = u["string_list_data"][0]
            print(f"{i}. {info.get('value')}  ->  {info.get('href')}")
        except:
            print(f"{i}. (format error)")
