bin_PROGRAMS = neverball neverputt
neverball_SOURCES = src/neverball.c src/game.c src/level.c src/gui.c
neverputt_SOURCES = src/neverputt.c src/putt.c src/gui.c

# Define libraries
neverball_LDADD = $(SDL2_LIBS) $(SDL2_TTF_LIBS) $(VORBIS_LIBS) $(JPEG_LIBS) $(CURL_LIBS)
neverputt_LDADD = $(SDL2_LIBS) $(SDL2_TTF_LIBS) $(VORBIS_LIBS) $(JPEG_LIBS)

# Include directories
AM_CPPFLAGS = $(SDL2_CFLAGS) $(SDL2_TTF_CFLAGS) $(VORBIS_CFLAGS) $(JPEG_CFLAGS) $(CURL_CFLAGS)
