CC      = g++
Options = -Wall -fexceptions -O2
#-------------------------------------------------------------------------------

Includes   = -ITools/Deflate       \
             -ITools/File          \
             -ITools/Gerber        \
             -ITools/Gerber/Gerber \
             -ITools/PDF           \
             -ITools/PDF/afm       \
             -ITools/PDF/pdf       \
             -ITools/String

Libraries  = 
LibInclude = 
#-------------------------------------------------------------------------------

Version = -DMAJOR_VERSION=1 -DMINOR_VERSION=3

Objects = obj/Tools/Deflate/JDeflate.o             \
          obj/Tools/File/JFile.o                   \
          obj/Tools/Gerber/JGerber.o               \
          obj/Tools/Gerber/Gerber/GerberAperture.o \
          obj/Tools/Gerber/Gerber/GerberLevel.o    \
          obj/Tools/Gerber/Gerber/GerberMacro.o    \
          obj/Tools/Gerber/Gerber/GerberRender.o   \
          obj/Tools/PDF/JPDF.o                     \
          obj/Tools/PDF/afm/afmParser.o            \
          obj/Tools/PDF/pdf/pdfAnnotation.o        \
          obj/Tools/PDF/pdf/pdfArray.o             \
          obj/Tools/PDF/pdf/pdfBool.o              \
          obj/Tools/PDF/pdf/pdfCatalogue.o         \
          obj/Tools/PDF/pdf/pdfContents.o          \
          obj/Tools/PDF/pdf/pdfCustomFont.o        \
          obj/Tools/PDF/pdf/pdfDest.o              \
          obj/Tools/PDF/pdf/pdfDictionary.o        \
          obj/Tools/PDF/pdf/pdfFont.o              \
          obj/Tools/PDF/pdf/pdfFontDescriptor.o    \
          obj/Tools/PDF/pdf/pdfFontFile.o          \
          obj/Tools/PDF/pdf/pdfFontMetrics.o       \
          obj/Tools/PDF/pdf/pdfForm.o              \
          obj/Tools/PDF/pdf/pdfHyperlink.o         \
          obj/Tools/PDF/pdf/pdfImage.o             \
          obj/Tools/PDF/pdf/pdfIndirect.o          \
          obj/Tools/PDF/pdf/pdfJPEG.o              \
          obj/Tools/PDF/pdf/pdfName.o              \
          obj/Tools/PDF/pdf/pdfNumber.o            \
          obj/Tools/PDF/pdf/pdfObject.o            \
          obj/Tools/PDF/pdf/pdfOpaque.o            \
          obj/Tools/PDF/pdf/pdfOutlineItems.o      \
          obj/Tools/PDF/pdf/pdfOutlines.o          \
          obj/Tools/PDF/pdf/pdfPage.o              \
          obj/Tools/PDF/pdf/pdfPages.o             \
          obj/Tools/PDF/pdf/pdfPNG.o               \
          obj/Tools/PDF/pdf/pdfRectangle.o         \
          obj/Tools/PDF/pdf/pdfResources.o         \
          obj/Tools/PDF/pdf/pdfStream.o            \
          obj/Tools/PDF/pdf/pdfString.o            \
          obj/Tools/PDF/pdf/pdfType1Font.o         \
          obj/Tools/PDF/pdf/pdfType3Font.o         \
          obj/Tools/String/JString.o               \
          obj/Resources/resource.res

Headers = Tools/Deflate/*.h       \
          Tools/File/*.h          \
          Tools/Gerber/*.h        \
          Tools/Gerber/Gerber/*.h \
          Tools/PDF/*.h           \
          Tools/PDF/afm/*.h       \
          Tools/PDF/pdf/*.h       \
          Tools/String/*.h
#-------------------------------------------------------------------------------

.PHONY: clean all
.SECONDARY:

all: bin/Gerber2pdf.exe

clean:
	rm -rf bin obj
#-------------------------------------------------------------------------------

# Binaries

bin/Gerber2pdf.exe: main.cpp main.h $(Objects) $(Headers)
	mkdir -p bin
	$(CC) $(Options) $(Version) $(Includes) $< $(Objects) -s $(LibInclude) $(Libraries) -o $@
#-------------------------------------------------------------------------------

# Objects

obj/%.o: %.cpp $(Headers)
	mkdir -p $(@D)
	$(CC) $(Options) $(Version) $(Defines) -c $(Includes) $< -o $@
#-------------------------------------------------------------------------------

# Resources

obj/%.res: %.rc
	mkdir -p $(@D)
	windres.exe -J rc -O coff -i $< -o $@
#-------------------------------------------------------------------------------
