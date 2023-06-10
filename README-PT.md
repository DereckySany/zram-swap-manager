# zRAM Swap Manager
Idiomas disponiveis: [Inglês](/README.md)

## Antes de Começar
    Este programa vem com absolutamente nenhuma garantia.
    Use-o por sua conta e risco.
    Consulte os documentos oficiais do kernel, 
    ArchWiki e/ou outras fontes respeitáveis para obter informações sobre a configuração da VM, zRAM, zswap e swap em geral.
    Muitos usuários devem ser atendidos pela configuração padrão.
    Os usuários mais avançados provavelmente irão querer ajustar uma ou duas coisas.

## Licença
    Direitos autorais/Copyright (C) 2021-2022, VR25

    Este programa é um software livre: você pode redistribuí-lo e/ou modificá-lo sob os termos da GNU General Public License publicada pela Free Software Foundation, seja a versão 3 da licença ou (a seu critério) qualquer versão posterior.

    Este programa é distribuído na esperança de que seja útil, mas SEM QUALQUER GARANTIA; mesmo sem a garantia implícita de COMERCIABILIDADE ou ADEQUAÇÃO PARA UM FIM ESPECÍFICO. Consulte a Licença Pública Geral GNU para obter mais detalhes.

    Você deve ter recebido uma cópia da Licença Pública Geral GNU junto com este programa. Caso contrário, consulte https://www.gnu.org/licenses/.
     
## Gerar um Zip Flechavél do Módulo Magisk
    sh /path/to/zip.sh

## Instalar/Atualizar
    Android (Magisk module)
      Flash the zip or run su -c sh /path/to/install.sh [--start]

    GNU/Linux
      sudo sh /path/to/install.sh [--start]

## Desinstalar
    Android
      su -c /data/adb/modules/zram-swap-manager/uninstall.sh [[--stop] [--keep-config]]

    GNU/Linux
      sudo zram-swap-manager-uninstall [[--stop] [--keep-config]]

## Configuração
    Android
      /data/adb/vr25/zram-swap-manager-data/config.txt

    GNU/Linux
      /etc/zram-swap-manager.conf

## Configuração padrão
    config_ver=202111230 # usado para correção; não modifique!

    comp_algorithm=auto # [auto] -> zstd (288) | lz4 (210) | lzo-rle (212) | lzo (211)
    comp_ratio=210 # [210], irrelevant when comp_algorithm=auto
    mem_percent=33 # [33], memory limit

    dynamic_swappiness=true # [true], swappiness <--> /proc/loadavg
    load_sampling_rate=60 # [60] read /proc/loadavg every x seconds
    high_load_threshold=90 # [90], %
    high_load_swappiness=80 # [80]
    medium_load_threshold=45 # [45], %
    medium_load_swappiness=90 # [90]
    low_load_threshold=0 # [0], %
    low_load_swappiness=100 # [100]

    vm="swappiness=80 page-cluster=0"

    # android's low memory killer (obsoleto em favor do lmkd em versões recentes do sistema operacional)
    # write /sys/module/lowmemorykiller/parameters/minfree "PARÂMETROS PERSONALIZADOS VÁ AQUI"

## Terminal
    Run zsm or zram-swap-manager for help.

## Referências/Benchmarks
|    Compressor	   | Version | Ratio	| Compression | Decompression |
|------------|------|--------|-------------|---------------|
|  zstd     |   1.3.4 -1   | 2.877	|   470 MB/s	|   1380 MB/s   |
| zlib      |   1.2.11 -1  | 2.743  |   110 MB/s  |   400 MB/s    |
| brotli    |   1.0.2 -0   | 2.701	|   410 MB/s	|   430 MB/s    |
| quicklz   |   1.5.0 -1   | 2.238	|   550 MB/s  |   710 MB/s    |
|  lzo1x    |   2.09 -1	   | 2.108	|   650 MB/s	|   830 MB/s    |
|    lz4    |   1.8.1	   | 2.101  |   750 MB/s  |   3700 MB/s   |
|   snappy  |   1.1.4      | 2.091	|   530 MB/s	|   1800 MB/s   |
|    lzf    |   3.6 -1	   | 2.077	|   400 MB/s	|   860 MB/s    |


## Notas/Dicas
    Em alguns sistemas Android, pode-se querer atrasar a inicialização para garantir que os padrões e/ou ajustes de terceiros sejam substituídos.
    Isso pode ser feito adicionando `sleep 90` ou uma lógica mais elaborada para configurar.

## Links

- [Donate - Airtm, username: ivandro863auzqg](https://app.airtm.com/send-or-request/send)
- [Donate - Liberapay](https://liberapay.com/vr25)
- [Donate - Patreon](https://patreon.com/vr25)
- [Donate - PayPal or Credit/Debit Card](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=iprj25@gmail.com&lc=US&item_name=VR25+is+creating+free+and+open+source+software.+Donate+to+suppport+their+work.&no_note=0&cn=&currency_code=USD&bn=PP-DonationsBF:btn_donateCC_LG.gif:NonHosted)
- [Facebook Page](https://fb.me/vr25xda)
- [Telegram Channel](https://t.me/vr25_xda)
- [Telegram Profile](https://t.me/vr25xda)
- [Upstream Repository](https://github.com/vr-25/zram-swap-manager)
- [XDA Thread](https://forum.xda-developers.com/t/zram-swap-manager-for-android-and-gnu-linux-systems.4352797)
