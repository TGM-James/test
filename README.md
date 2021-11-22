1. V1
nrfutil settings generate --family NRF52 --application BS-SW-D01-01.hex --application-version 1 --bootloader-version 1 --bl-settings-version 2 setting.hex
mergehex --merge TGM_Bootloader.hex setting.hex --output bl_temp.hex
mergehex --merge bl_temp.hex BS-SW-D01-01.hex s132_nrf52_7.2.0_softdevice.hex --output BS-SW-D01-01_V1_OTA.hex
nrfutil pkg generate --hw-version 52 --sd-req 0xCB,0x101 --softdevice s132_nrf52_7.2.0_softdevice.hex --sd-id 0x101 --application BS-SW-D01-01.hex --application-version 1 --key-file priv.pem BS-SW-D01-01_V1_OTA.zip