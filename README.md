# nirvana(Illumina Connected Annotations)

## 1:准备credential file 

    {
      "MyIlluminaApiKey": "<your Illumina account api key>",#登录https://accounts.login.illumina.com/获得
      "DragenSerialNo": "<your Dragen server serial no.>"#dragen_info -b | grep Serial获得
    }

## 2.下载数据库

    [INSTALL_PATH]/DataManager download -r GRCh38 \
    --credentials-file [path to credential file] \
    --dir [path to dir] \
    --versions-config [path to resource directory]/all_annotations_GRCh38.json

## 3.注释

**FASTQ-in:**

    --enable-variant-annotation true \
    --variant-annotation-data /path/to/your/NirvanaData \
    --variant-annotation-assembly GRCh38 \
    --annotation-data-config /path/to/resources/annotation/all_annotations_GRCh38.json
**VCF-in:**

    <INSTALL_PATH>/share/nirvana/Nirvana -c [path to data dir]/Cache \
    -r [path to data dir]/References/Homo_sapiens.GRCh38.Nirvana.dat \
    --sd [path to data dir]/SupplementaryAnnotation/GRCh38 \
    -l [path to credential file] --versions-config [path to resource directory]/all_annotations_GRCh38.json
    -i <input_VCF> -o <output_prefix>

