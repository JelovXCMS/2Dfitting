ROOTCFLAGS	=	$(shell root-config --cflags)
ROOTGLIBS		=	$(shell root-config --glibs)

CPP					=	g++
CPPFLAGS		=	-g -fPIC -Wno-deprecated -O2 -ansi
LD					=	g++
LDFLAGS			=	-g
SOFLAGS			=	-shared

CPPFLAGS		+= $(ROOTCFLAGS)
NGLIBS			=	$(ROOTGLIBS)
#### in LXPLUS
#NGLIBS      += -L/afs/cern.ch/user/k/kyolee/public/root_v5.28.00h/lib -lMathMore -lMinuit -lRooFit -lRooFitCore -lFoam
NGLIBS      += -L/cvmfs/cms.cern.ch/slc6_amd64_gcc493/lcg/root/6.06.00-ikhhed4/lib -lMathMore -lMinuit -lRooFit -lRooFitCore -lFoam
#### in KUNPL
#NGLIBS      += -L/data/root-v5.28.00h/lib -lMathMore -lMinuit -lRooFit -lRooFitCore -lFoam
#NGLIBS      += -L/data/root-v6.04.02h/lib -lMathMore -lMinuit -lRooFit -lRooFitCore -lFoam
GLIBS				= $(filter-out -lNew, $(NGLIBS))

INCLUDEDIR	=	./
CPP					+= -I$(INCLUDEDIR)
### in LXPLUS
#CPP         += -I/afs/cern.ch/user/k/kyolee/public/root_v5.28.00h/include
CPP         += -I/cvmfs/cms.cern.ch/slc6_amd64_gcc493/lcg/root/6.06.00-ikhhed4/include
#### in KUNPL
#CPP         += -I/data/root-v5.28.00h/include
#CPP         += -I/data/root-v6.04.02/include
OUTLIB			= ./

.SUFFIXES:	.cc,.C,.hh,.h
.PREFIXES:	./

RooHistPdfConv.o: $(INCLUDEDIR)/RooHistPdfConv.cpp
	$(CPP) $(CPPFLAGS) -c -o $(OUTLIB)/libRooHistPdfConv.o $(NGLIBS) $<

Fit2DData:	$(INCLUDEDIR)fit2DData.cpp
	$(CPP) $(CPPFLAGS) -o Fit2DData $(OUTLIB)/*.o $(GLIBS) $ $<

Fit2DDataPASP:	$(INCLUDEDIR)fit2DData_PASP.cpp
	$(CPP) $(CPPFLAGS) -o Fit2DDataPASP $(OUTLIB)/*.o $(GLIBS) $ $<

Fit2DDataPASBPASP:	$(INCLUDEDIR)fit2DData_PASB_PASP.cpp
	$(CPP) $(CPPFLAGS) -o Fit2DDataPASBPASP $(OUTLIB)/*.o $(GLIBS) $ $<


clean:
	rm -f $(OUTLIB)*.o $(OUTLIB)*.so
