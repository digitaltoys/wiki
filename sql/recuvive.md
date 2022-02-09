### recucive
```
SELECT p1.cmnt_seq_no, p1.prnt_cmnt_no, p1.reg_dtm, p1.cmnt_cn,
	(case 
		when P2.cmnt_seq_no is null then lpad(convert(P1.cmnt_seq_no, char(4)), 4, '0')
		when P3.cmnt_seq_no is null then concat(lpad(convert(P2.cmnt_seq_no, char(4)), 4, '0'), lpad(convert(P1.cmnt_seq_no, char(4)), 4, '0'))
        else concat(lpad(convert(P3.cmnt_seq_no, char(4)), 4, '0'), lpad(convert(P2.cmnt_seq_no, char(4)), 4, '0'), lpad(convert(P1.cmnt_seq_no, char(4)), 4, '0'))
	end) as seq,
	(case 
		when P2.cmnt_seq_no is null then 1
		when P3.cmnt_seq_no is null then 2
		else 3
	end) as depth
FROM tmb_cmnt_cmnt P1
LEFT outer join tmb_cmnt_cmnt P2
on P1.prnt_cmnt_no = P2.cmnt_seq_no
left outer join tmb_cmnt_cmnt P3
on P2.prnt_cmnt_no = P3.cmnt_seq_no
order by seq;
```
