TESTS := test-sinc-lowest \
	test-snr-sinc-lowest \
	test-sinc-lower \
	test-snr-sinc-lower \
	test-sinc \
	test-snr-sinc \
	test-sinc-higher \
	test-snr-sinc-higher \
	test-sinc-highest \
	test-snr-sinc-highest

CFLAGS += -O3 -ffast-math -g -Wall -pedantic -march=native -std=gnu99 -DRESAMPLER_TEST
LDFLAGS += -lm

all: $(TESTS)

resampler-sinc.o: ../resampler.c
	$(CC) -c -o $@ $< $(CFLAGS)

sinc-lowest.o: ../sinc.c
	$(CC) -c -o $@ $< $(CFLAGS) -DSINC_LOWEST_QUALITY

sinc-lower.o: ../sinc.c
	$(CC) -c -o $@ $< $(CFLAGS) -DSINC_LOWER_QUALITY

sinc.o: ../sinc.c
	$(CC) -c -o $@ $< $(CFLAGS)

sinc-higher.o: ../sinc.c
	$(CC) -c -o $@ $< $(CFLAGS) -DSINC_HIGHER_QUALITY

sinc-highest.o: ../sinc.c
	$(CC) -c -o $@ $< $(CFLAGS) -DSINC_HIGHEST_QUALITY

test-sinc-lowest: sinc-lowest.o ../utils.o main.o resampler-sinc.o
	$(CC) -o $@ $^ $(LDFLAGS)

test-snr-sinc-lowest: sinc-lowest.o ../utils.o snr.o resampler-sinc.o
	$(CC) -o $@ $^ $(LDFLAGS)

test-sinc-lower: sinc-lower.o ../utils.o main.o resampler-sinc.o
	$(CC) -o $@ $^ $(LDFLAGS)

test-snr-sinc-lower: sinc-lower.o ../utils.o snr.o resampler-sinc.o
	$(CC) -o $@ $^ $(LDFLAGS)

test-sinc: sinc.o ../utils.o main.o resampler-sinc.o
	$(CC) -o $@ $^ $(LDFLAGS)

test-snr-sinc: sinc.o ../utils.o snr.o resampler-sinc.o
	$(CC) -o $@ $^ $(LDFLAGS)

test-sinc-higher: sinc-higher.o ../utils.o main.o resampler-sinc.o
	$(CC) -o $@ $^ $(LDFLAGS)

test-snr-sinc-higher: sinc-higher.o ../utils.o snr.o resampler-sinc.o
	$(CC) -o $@ $^ $(LDFLAGS)

test-sinc-highest: sinc-highest.o ../utils.o main.o resampler-sinc.o
	$(CC) -o $@ $^ $(LDFLAGS)

test-snr-sinc-highest: sinc-highest.o ../utils.o snr.o resampler-sinc.o
	$(CC) -o $@ $^ $(LDFLAGS)

%.o: %.c
	$(CC) -c -o $@ $< $(CFLAGS)

clean:
	rm -f $(TESTS)
	rm -f *.o
	rm -f ../*.o

.PHONY: clean

