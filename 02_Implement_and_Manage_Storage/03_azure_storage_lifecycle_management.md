# 🔁 Azure Storage Lifecycle Management

---

## 📌 What is Lifecycle Management?

Azure Storage Lifecycle Management helps **automate moving** or **deleting blob data** based on rules.

This helps:
- Save costs
- Reduce manual work
- Manage data retention and archival

---

## ⚙️ Key Features

- Automatically **transition blobs** between access tiers:  
  🔸 Hot → Cool → Cold → Archive

- Automatically **delete blobs** after a set number of days

- Apply rules based on:
  - Blob type (Block, Append)
  - Container name
  - Blob name prefix
  - Last modified date
  - Tags (if using blob index tagging)

---

## 📁 Rule Example Use Cases

| Scenario                                      | Action                                     |
|----------------------------------------------|--------------------------------------------|
| Move blobs not modified in 30 days to Cool   | Tier to Cool after 30 days                 |
| Archive blobs not modified in 90 days        | Tier to Archive after 90 days              |
| Delete blobs not modified in 180 days        | Delete after 180 days                      |
| Apply rule to logs/ prefix only              | Use name prefix filter like `logs/`        |
| Delete previous versions after 60 days       | Apply to previous versions only            |

---

## 🧠 How It Works

- Rules are evaluated **once per day**
- Blobs must be in **Hot/Cool/Cold** tier to be moved to **Archive**
- Rules are written in **JSON format** (or via portal)

---

## 📘 JSON Rule Examples

### 1. Move to Cool after 30 days

```json
{
  "rules": [
    {
      "name": "MoveToCool",
      "enabled": true,
      "type": "Lifecycle",
      "definition": {
        "filters": {
          "blobTypes": ["blockBlob"]
        },
        "actions": {
          "baseBlob": {
            "tierToCool": {
              "daysAfterModificationGreaterThan": 30
            }
          }
        }
      }
    }
  ]
}
```

---

## 🛑 Important Notes

- Lifecycle management **does NOT move blobs from Archive** to other tiers.
- Lifecycle policy can only be applied to **Block and Append blobs**.
- If **multiple rules apply to the same blob on the same day**, and they have **conflicting actions** (e.g., move to Cool vs. Archive), then:
  > ✅ **Azure chooses the action that results in the lowest storage cost.**
- Archive tiered blobs are **read-only** until rehydrated.

---

## 📘 Exam Tips

- Know what actions are possible (tier change, delete)
- Understand when and how rules are triggered
- Be aware that blobs in **Archive** must be rehydrated manually
- Expect scenario-based questions (e.g., “Reduce cost by archiving after 60 days”)

---