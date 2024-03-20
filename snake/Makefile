RAYLIB_PATH="${HOME}/raylib"

.PHONE: all
all: build dist serve

build:
	emcc -o snake.html snake.c -Os -Wall ${RAYLIB_PATH}/src/libraylib.a -I. -I${RAYLIB_PATH}/src -L. -L$RAYLIB_PATH/src -s USE_GLFW=3 -s ASYNCIFY --shell-file ${RAYLIB_PATH}/src/minshell.html -DPLATFORM_WEB --preload-file bloom.fs -s EXPORTED_FUNCTIONS='["_SetWindowSize", "_main", "_malloc"]'

dist:
	cp snake.html ../index.html
	cp snake.wasm ../
	cp snake.data ../
	cp snake.js ../

.PHONY: clean
clean:
	rm snake.html snake.js snake.wasm
	rm ../index.html ../snake.js ../snake.wasm

.PHONY: serve
serve:
	miniserve ../ --index index.html
