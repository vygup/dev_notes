```sql

CREATE [OR REPLACE] FUNCTION scheme.procedure_name ()
	[RETURNS] 
	LANGUAGE 
	VOLATILE 
AS
$$
[<<Метка>>]
[DECLARE]
BEGIN
END;
$$	
	

|OR REPLACE Помагает обновлять функцию	
|(имя_аргумента тип_аргумента) Режим аргумента --(default) дает необязательный эоемент
	|(по дефолту IN--входной)
	|OUT 
	|INOUT
	|VARIADIC--переменный
RETURNS --тип результата 
	|VOID --ничего не возвращать
	|SETOF --возвращает множество, а не едингственный элемент
	|RECORD --если выходных параметров несколько, либо тип единственного выходного параметра
	|TABLE (имя_столбца тип_солбца)
LANGUAGE --имя_языка
	|sql
	|plpgsql
	|c
	|internal
default VOLATILE
	|IMMUTABLE--постоянная функция 
	|STABLE--стабильная функция 
	|VOLATILE--изменчивая функция 
DECLARE --объявления(переменные)
BEGIN --
END --финальный, завершающий тело функции не требует';', в ост. случаях необходимо
<<Метка>>-- для определения внешнего блока
	 /*
	CREATE FUNCTION somefunc() RETURNS integer AS $$
	<< outerblock >>
	DECLARE
	quantity integer := 30;
	BEGIN
	RAISE NOTICE 'Сейчас quantity = %', quantity;  -- Выводится 30
	quantity := 50;
	--
	-- Вложенный блок
	--
	DECLARE
	quantity integer := 80;
	BEGIN
	RAISE NOTICE 'Сейчас quantity = %', quantity;  -- Выводится 80
	RAISE NOTICE 'Во внешнем блоке quantity = %', outerblock.quantity;  -- Выводится 50
	END;

	RAISE NOTICE 'Сейчас quantity = %', quantity;  -- Выводится 50

	RETURN quantity;
	END;
	$$ LANGUAGE plpgsql;
	*/







CREATE OR REPLACE FUNCTION scheme.name_func()
RETURNS void
LANGUAGE plpgsql
VOLATILE
AS $$

declare

text_1      text    :=  'text';
text_2      text;
text_proc   text;
cntg        bigint  default 0;

begin

---

PERFORM ;-- запуск процедуры
SELECT 'text2' INTO text_2; --запись в переменную [FROM scheme.table]--значение из таблицы
SELECT scheme.proc_name([значения(Переменные)]) INTO text_proc;
EXECUTE 'SELECT count(1) FROM scheme.'||table_ INTO cnte;
descr := 'table=count_rows: '||espd_table||' ['||cnte::TEXT||']';

EXECUTE FORMAT (query_text);

---

if условия
then если 1
else если 0
end if;

---

EXECUTE (SELECT FROM scheme.table) -- на выход 1 - есть данные, 0 - нет данных

- -----------------------Обработчик ошибок---------------------
exception
when others then
perform scheme.proc_name('ERROR', sqlstate, sqlerrm);
------------------------Обработчик ошибок---------------------

end;
$$
EXECUTE ON ANY;

```
