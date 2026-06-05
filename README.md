Doc note maker

INIT Project

# Créer un env virtuel

python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# update package

pip freeze > requirements.txt

# launch zensical local

zensical serve
