提示：让 test_blank_name_exits_2 通过，只改 src/greetlab/cli.py。
改动：在 main 中增加空白姓名检查，使用 argparse.error 以 SystemExit(2) 退出。
验证：PYTHONPATH=src python3 -m pytest，1 passed。
