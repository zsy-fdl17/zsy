include ../config

all: qpa_symb.cmo qpa_run.cmo qpa_main.cmo
	$(ZELUC) qpa_run.zls
	$(OCAMLC) $(OCAMLFLAGS) -o qpa.byte $(INCLUDES) \
	    graphics.cma -I $(ZLLIB) $(ZLSTDLIBS) $(ZLEXTRALIBS) $^

qpa_symb.ml archi.zls: qpa.zls
	$(ZELUC) -symb archi qpa.zls
	$(ZELUC) qpa_symb.zls

qpa_run.zls: qpa.zls archi.zls runtime.zls
	$(ZELUC) archi.zls
	cat archi.zls runtime.zls > qpa_run.zls
	$(ZELUC) qpa_run.zls

qpa_main.cmo: INCLUDE += $(SUNDIALS)

qpa_run.ml qpa_main.ml: qpa_run.zls
	$(ZELUC) -I $(ZLLIB) -s main -sampling 0 qpa_run.zls
	mv main.ml qpa_main.ml

clean:
	-@rm -f qpa_symb.*
	-@rm -f archi.*
	-@rm -f qpa_run.*
	-@rm -f qpa_main.*
	-@rm -f *~ *.zci *.cm*

realclean cleanall: clean
	-@rm -f qpa.byte
