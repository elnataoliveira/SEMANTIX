### basics commands

``` sh
create 'controle','produto','fornecedor'
put 'controle','1','produto:nome','ram'
put 'controle','2','produto:nome','hd'
put 'controle','3','produto:nome','mouse'
scan 'controle'
put 'controle','3','produto:qntd','150'
put 'controle','2','produto:qntd','50'
put 'controle','1','produto:qntd','100'
put 'controle','2','fornecedor:estado','MG'
put 'controle','1','fornecedor:estado','SP'
put 'controle','3','fornecedor:estado','SP'
put 'controle','1','fornecedor:nome','TI Comp'
put 'controle','2','fornecedor:nome','Peças PC'
put 'controle','3','fornecedor:nome','Inf Tec'

 scan 'controle'
  list
  describe 'controle'
 count 'controle'
  alter 'controle', {NAME=>'produto',VERSIONS=>3}
  scan 'controle'
    describe 'controle'
    put 'controle','2','produto:qntd','200'
    get 'controle','2',{COLUMNS=>'produto', VERSIONS=>2}
   scan 'controle', {COLUMN=>'fornecedor:estado'}
 scan 'controle', {COLUMN=>'fornecedor:estado', LIMIT=>5}
 scan 'controle', {COLUMN=>'fornecedor:estado', LIMIT=> 5, FILTER => "ValueFilter(=, 'binary:SP')"}
  deleteall 'controle','1'
   deleteall 'controle','3'
   count 'controle'
  delete 'controle', '2', 'fornecedor:estado'
  scan 'controle'
   
  
```
