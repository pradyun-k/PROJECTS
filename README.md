# PROJECTS NO-1
🛡️ PhishVision - Simple Email Phishing Detector by Pradyun

Language: Python 3

import re

def check_phishing_signs(email_text): phishing_keywords = [ "urgent", "verify your account", "update your information", "click here", "login now", "account suspended", "password expired", "bank", "lottery", "prize" ]

suspicious_links = re.findall(r"https?://[\w./-]+", email_text)
keyword_hits = [word for word in phishing_keywords if word in email_text.lower()]

print("\n📄 EMAIL ANALYSIS RESULT")
print("-------------------------")

if suspicious_links:
    print(f"🔗 Suspicious Links Found:")
    for link in suspicious_links:
        print(f" - {link}")
else:
    print("✅ No suspicious links detected.")

if keyword_hits:
    print(f"⚠️ Phishing Keywords Detected:")
    for word in keyword_hits:
        print(f" - {word}")
else:
    print("✅ No phishing keywords detected.")

if suspicious_links or keyword_hits:
    print("❌ WARNING: This email might be a phishing attempt!")
else:
    print("✅ This email looks clean.")

if name == "main": print("\n=== 🛡️ Welcome to PhishVision by Pradyun ===") email_input = input("\n📥 Paste the email text to scan for phishing: \n\n") check_phishing_signs(email_input)
