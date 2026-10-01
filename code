import platform
import os
import socket
import getpass
import json
import shutil

def sysinfo():
    
    os_name = platform.system()


    if os_name =='Windows':
        root_path = "C:\\"
    else:
        root_path = "/"
    
    if os.path.exists(root_path):
        total, used, free = shutil.disk_usage(root_path)
        total = f"{round(total/(1024**3),2)} GB"
        used = f"{round(used/(1024**3),2)} GB"
        free = f"{round(free/(1024**3),2)} GB"
    else:
        total, used, free = "Не удалось определить параметры памяти\n"


    sysinformation = {
        "Операционная система": os_name,
        "Версия операционной системы": platform.version(),
        "Релиз операционной системы": platform.release(),
        "Процессор": platform.processor() or platform.machine(),
        "Память на диске": total,
        "Заполненная память на диске": used,
        "Свободная память на диске": free,
        "Имя устройства": socket.gethostname(),
        "Имя пользователя": getpass.getuser(),
        "Версия Python": platform.python_version()
    }
    
    filename = "systeminfo.json"
    with open(filename, "w", encoding="utf-8") as f:
        json.dump(sysinformation, f, indent=4, ensure_ascii=False)

    print(json.dumps(sysinformation, indent=4, ensure_ascii=False))
    print(f"Файл: {os.path.abspath(filename)}")

if __name__ == "__main__":
    sysinfo()
