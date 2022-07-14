## bigquery bq 사용법
bq --location=US load --source_format=CSV --autodetect dataset.table-name ./export.csv.gz



문제 있는 레코드는 건너뛰도록 설정
>--max_bad_records=20

Null값을 문자열 null로 표현하고 있을 때
>bq --location=US load --null_marker=NULL --source_format=CSV --autodetect dataset.table-name ./export.csv.gz

기존 테이블 데이터 교체
>bq --location=US load --null_marker=NULL --source_format=CSV --autodetect dataset.table-name ./export.csv.gz

기존 테이블에 append 하려면 --replace=false 를 지정


테이블 스키마 확인
>bq show --format prettyjson --schema dataset.table-name

테이블 복사 - ctas 보다 빠르고 쿼리 비용도 발생하지 않음 --append_table 옵션을 지정하면 첨부도 가능하다.
>bp cp source-dataset:table-name target-dataset:table-name

