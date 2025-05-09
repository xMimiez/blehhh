import json
import time
import random
import requests

# MAKE A FILE WITH YOUR USERTOKEN "secret.json"
# MAKE A FILE WITH YOUR USERTOKEN "secret.json"
# MAKE A FILE WITH YOUR USERTOKEN "secret.json"
# MAKE A FILE WITH YOUR USERTOKEN "secret.json"
# MAKE A FILE WITH YOUR USERTOKEN "secret.json"
# MAKE A FILE WITH YOUR USERTOKEN "secret.json"
# MAKE A FILE WITH YOUR USERTOKEN "secret.json"

with open("secret.json", "r") as f:
    data = json.load(f)
    user_token = data["user_token"]


headers = {
    "Authorization": user_token,
    "Content-Type": "application/json"
}


statuses = [
    # {"emoji_name": "EMOJI NAME", "emoji_id": "EMOJI ID", "text": "TEXT", "animated": TRUE OR FALSE},
    

]


def is_user_online():
    response = requests.get("https://discord.com/api/v9/users/@me/settings", headers=headers)
    if response.status_code == 200:
        status = response.json().get("status", "")
        print(f"👤 Current status: {status}")
        return status == "online" # can change to any status (dnd, idle, invisible, online)
    else:
        print(f"⚠️ Failed to check user status: {response.status_code}")
        return False

def update_status(status_info):
    payload = {
        "custom_status": {
            "text": status_info["text"],
            "emoji_name": status_info["emoji_name"],
            "emoji_id": status_info["emoji_id"]
        }
    }
    response = requests.patch("https://discord.com/api/v9/users/@me/settings", headers=headers, json=payload)
    if response.status_code == 200:
        print(f"✅ Updated status to: {status_info['emoji_name']} | {status_info['text']}")
    else:
        print(f"❌ Error updating status: {response.status_code}: {response.text}")


while True:
    if is_user_online():
        for status in statuses:
            update_status(status)
            delay = random.randint(10, 15)
            print(f"⏱ Waiting {delay} seconds before next update...")
            time.sleep(delay)
    else:
        print("🛑 User not online. Retrying in 30 seconds...")
        time.sleep(30)
