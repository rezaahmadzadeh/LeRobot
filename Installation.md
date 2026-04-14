# Installation

## Linux (Ubuntu)

Here are the steps for installing the robot software:
1. according to the documentation, the software requires Python >= 3.12
2. make a virtual environment `python -m venv lerobot_env`
3. activate the virtual environment `source lerobot_env/bin/activate`
4. install robot software `pip install lerobot`
5. if you see error regarding scservo_sdk, you need to install `pip install -U 'lerobot[feetech]'`
