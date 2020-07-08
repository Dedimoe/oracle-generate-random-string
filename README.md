# oracle-generate-random-string
Oracle database plsql for generating random string

```
create or replace function d_random_str(lmax number) return varchar2 
is
    s varchar2(4000);
begin
    for i in 1..lmax loop
        s := s || dbms_random.string(
            case when dbms_random.value(0, 1) < 0.5 then 'l' else 'x' end, 1
        );
    end loop;
    return s;
end;
```

### usage

```
select d_random_str(10) from dual;
```
output:
```
P8dVNFnSes
```
