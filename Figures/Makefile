root := ../../smartnoise-sdk/sdk/opendp/smartnoise/
targets := Query Logical Numeric QueryParser PrivateReader Expression SqlExpression SqlReader Rewriter Validate Tokens

define generate_all
	pyreverse -o eps -S -A -m y $(addsuffix $(strip $(2)),$(root))  && mv classes.eps $(1).eps
	pyreverse -o png -S -A -m y $(addsuffix $(strip $(2)),$(root))  && mv classes.png $(1).png
	touch $(1)
endef

define generate_class
	pyreverse -o eps -S -A -m y -c $(1) $(addsuffix $(strip $(2)),$(root)) 
	pyreverse -o png -S -A -m y -c $(1) $(addsuffix $(strip $(2)),$(root)) 
	touch $(1)
endef

main: $(targets)

QueryParser:
	$(call generate_class, QueryParser, sql/parse.py)

Rewriter:
	$(call generate_all, Rewriter, sql/private_rewriter.py)

PrivateReader:
	$(call generate_all, PrivateReader, sql/private_reader.py)

SqlReader:
	$(call generate_all, SqlReader, sql/reader/)

Validate:
	$(call generate_all, Validate, _ast/validate.py)

Query:
	$(call generate_all, Query, _ast/ast.py)

Tokens:
	$(call generate_all, Tokens, _ast/tokens.py)

Expression:
	$(call generate_all, Expression, _ast/expression.py)

SqlExpression:
	$(call generate_all, SqlExpression, _ast/expressions/sql.py)

Logical:
	$(call generate_all, Logical, _ast/expressions/logical.py)

Numeric:
	$(call generate_all, Numeric, _ast/expressions/numeric.py)

clean:
	rm -f *.eps
	rm -f *.png
	rm -f $(targets)