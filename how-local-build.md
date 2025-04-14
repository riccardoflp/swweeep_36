## local build guide

clone zmk firmware
```
git clone https://github.com/zmkfirmware/zmk.git
```

create zmk python virtula enviroment
```
cd zmk
python3 -m venv .venv
source .venv/bin/activate
```

install zephyr
```
pip install west
west init -l app/
west update
west zephyr-export
pip install -r zephyr/scripts/requirements-base.txt
```

test build
```
cd app
west build -b planck_rev6
```

build swweeep_36
```
west build -d build/swweeep/right --pristine -b "nice_nano_v2" -- -DSHIELD=swweeep_right -DZMK_EXTRA_MODULES="/yourpath/swweeep_36/"
west build -d build/swweeep/left --pristine -b "nice_nano_v2" -- -DSHIELD=swweeep_left -DZMK_EXTRA_MODULES="/yourpath/swweeep_36/"
west build -d build/swweeep/reset --pristine -b "nice_nano_v2" -- -DSHIELD=settings_reset -DZMK_EXTRA_MODULES="/yourpath/swweeep_36/"
```
