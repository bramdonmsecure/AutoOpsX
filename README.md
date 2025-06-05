#!/usr/bin/env python3
"""
AutoOpsX - System Health Monitor

Checks CPU, memory, and disk usage.
Alerts if thresholds exceeded.
Cross-platform friendly for Windows & Linux.
"""

import psutil
import platform
import datetime
import logging
import sys
import os

# Configurable thresholds
CPU_THRESHOLD = 85  # percent
MEM_THRESHOLD = 80  # percent
DISK_THRESHOLD = 90  # percent

# Setup logging
logging.basicConfig(
    filename='autoopsx_health.log',
    level=logging.INFO,
    format='%(asctime)s - %(levelname)s - %(message)s'
)

def alert(message):
    """
    Placeholder for alert mechanism.
    Replace print with email, Slack, or other alerting system.
    """
    print(f"⚠️ ALERT: {message}")
    logging.warning(message)

def check_cpu():
    cpu = psutil.cpu_percent(interval=1)
    logging.info(f"CPU Usage: {cpu}%")
    if cpu > CPU_THRESHOLD:
        alert(f"High CPU Usage detected: {cpu}%")

def check_memory():
    mem = psutil.virtual_memory()
    logging.info(f"Memory Usage: {mem.percent}%")
    if mem.percent > MEM_THRESHOLD:
        alert(f"High Memory Usage detected: {mem.percent}%")

def check_disk():
    # Determine root path based on OS
    if platform.system() == "Windows":
        root_partition = os.getenv('SystemDrive', 'C:') + '\\'
    else:
        root_partition = '/'
    
    disk = psutil.disk_usage(root_partition)
    logging.info(f"Disk Usage on {root_partition}: {disk.percent}%")
    if disk.percent > DISK_THRESHOLD:
        alert(f"High Disk Usage detected on {root_partition}: {disk.percent}%")

def system_info():
    info = {
        "Platform": platform.system(),
        "Platform Release": platform.release(),
        "Platform Version": platform.version(),
        "Hostname": platform.node(),
        "Processor": platform.processor(),
        "Python Version": platform.python_version(),
        "Check Time": datetime.datetime.now().isoformat()
    }
    for k, v in info.items():
        logging.info(f"{k}: {v}")
    print(f"System Info: {info}")

def main():
    print("AutoOpsX System Health Check Starting...")
    system_info()
    check_cpu()
    check_memory()
    check_disk()
    print("Check complete. Logs saved to autoopsx_health.log")

if __name__ == "__main__":
    try:
        main()
    except Exception as e:
        logging.error(f"Fatal error: {e}")
        print(f"Fatal error: {e}")
        sys.exit(1)