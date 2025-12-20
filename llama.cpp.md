## Running LLMs on phone

Termux is an Android app that lets you run a Linux-like terminal on your phone. Among many things you can do with Termux, one interesting thing is running the llama-cpp project directly on your device.

```sh
pkg install llama-cpp
```

The Termux team recently implemented the [llama-cpp](https://github.com/termux/termux-packages/blob/master/packages/llama-cpp) package, which makes building llama-cpp much easier, now you can install it with a single command. In the past, I had to follow the official [build guide](https://github.com/ggml-org/llama.cpp/blob/master/docs/android.md), but this package simplifies the process. This is a handy tip if you want to run local LLM models on your Android device.

After package install, start the model server:

```sh
llama-server -hf Qwen/Qwen3-0.6B-GGUF --port 11434 --jinja -c 20000
```

This command downloads the model from Hugging Face, starts a server exposing an API on port 11434, provides a frontend interface using Jinja templates, and allocates 20,000 tokens of context.

Once running, you can interact with the model and start chat sessions directly from your phone

One thing I found interesting is that the termux [build script](https://github.com/termux/termux-packages/blob/master/packages/llama-cpp/build.sh) uses a host toolchain to precompile Vulkan shaders, which is useful for devices with weaker CPUs, but it excludes 32-bit architectures, so it targets 64-bit ARM and x86_64 devices.
