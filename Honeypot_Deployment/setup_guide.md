# Cowrie Honeypot Deployment Guide

This guide walks through the setup of **Cowrie**, a medium-interaction SSH and Telnet honeypot that logs brute-force attacks and shell interaction. Ideal for analyzing attacker behavior in a controlled lab.

---

## Prerequisites

- Ubuntu 20.04+ installed (physical or virtual)
- Python 3.6+
- Internet access
- 2+ GB RAM, 20 GB disk

---

## Setup Steps

### 1. System Preparation

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git python3-venv python3-pip libssl-dev libffi-dev build-essential libpython3-dev libyaml-dev libxslt1-dev -y