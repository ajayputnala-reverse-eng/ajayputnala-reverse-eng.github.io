---
title: A Beginner's Guide to Setting Up Ghidra
date: 2026-05-06 22:38:00 +0530
categories: [Tools, Static Analysis]
tags: [ghidra, reverse-engineering, beginner]
---

## Welcome to the Workbench

Before we can start taking software apart, we need the right tools. Today, we are setting up **Ghidra**, a powerful, open-source software reverse engineering (SRE) framework originally created by the NSA.

### What is a Disassembler?

At its core, a disassembler takes compiled machine code (the 1s and 0s that a computer understands) and translates it back into assembly language, which is somewhat readable by humans. Ghidra goes a step further by including a **decompiler**, which attempts to translate that assembly back into high-level C-like pseudocode. 

### Step 1: Prerequisites

Before downloading Ghidra, you must have Java installed on your system. 
1. Open your terminal or command prompt.
2. Type `java -version` to ensure it is installed and recognized. (You need JDK 11 or later).

### Step 2: Downloading Ghidra

1. Navigate to the official [Ghidra GitHub Releases page](https://github.com/NationalSecurityAgency/ghidra/releases).
2. Download the latest `.zip` file.
3. Extract the contents to a safe directory on your machine (e.g., `C:\Tools\Ghidra`).

### Step 3: Running for the First Time

Unlike traditional software, Ghidra doesn't need to be "installed" into your system registry. It runs directly from the extracted folder.
* **Windows:** Double-click `ghidraRun.bat`
* **Linux/macOS:** Run `./ghidraRun` from your terminal.

Once it opens, you will be greeted by the project manager window. You are now ready to create your first project and import a binary for analysis!
