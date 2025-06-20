# 📁 Droply — A Dropbox-like Cloud Storage App

Droply is a modern, full-stack file-Storage built with **Next.js**, **Clerk authentication**, **Neon DB**, **Drizzle ORM**, and **ImageKit** for file uploads. It allows users to securely upload, organize, preview, and download their files and folders with rich features like starring, trash management, and more.

---

## ✨ Features

- 🔐 **Authentication**: Secure user login/signup with [Clerk.dev](https://clerk.dev)
- 📤 **File Upload**:
  - Upload **images and documents** up to **5MB**
  - Supported extensions: `All image extension`, `.PDF`, `.DOC`, `.DOCX`, `.XLS`, `.XLSX`, `.TXT`.
 
- 📁 **Folder Management**:
  - Users can **create folders**
  - Upload files directly into folders
  - Uses **self-relation** in the database to represent folder nesting
- ⭐ **Starred Items**:
  - Mark important files/folders as starred
- 🗑️ **Trash System**:
  - Soft-delete: move files/folders to trash
  - Restore or permanently delete
  - **Empty Trash** to clear all deleted items at once
- 🖼️ **File & Image Preview**:
  - View images and documents (PDF, JPG, PNG, etc.) directly in the app
- ⬇️ **Download Files**:
  - Users can download uploaded files anytime

---

## 🛠 Tech Stack

| Layer            | Technology |
|------------------|------------|
| Frontend & Backend  | [Next.js](https://nextjs.org/) |
| Authentication   | [Clerk](https://clerk.dev) |
| Database         | [Neon DB](https://neon.tech) |
| ORM              | [Drizzle ORM](https://orm.drizzle.team/) |
| File Storage     | [ImageKit](https://imagekit.io) |

---

## 🚀 Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/yourusername/droply.git
cd droply
