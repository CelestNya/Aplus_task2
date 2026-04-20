> uv run main.py

<details>
<summary>启动日志</summary>

```sh
=== vLLM VLM 对话终端 ===
模型: D:\Resources\Models\Qwen2.5-7B-Instruct-AWQ
系统提示: 你是通义千问，由阿里云开发，是一个有用的助手。
命令: /image <图片路径> - 附加图片提问
输入 exit 退出

INFO 04-20 20:13:13 [model.py:554] Resolved architecture: Qwen2ForCausalLM
INFO 04-20 20:13:13 [model.py:1685] Using max model len 4096
INFO 04-20 20:13:13 [awq_marlin.py:252] The model is convertible to awq_marlin during runtime. Using awq_marlin kernel.
INFO 04-20 20:13:14 [scheduler.py:238] Chunked prefill is enabled with max_num_batched_tokens=2048.
INFO 04-20 20:13:14 [vllm.py:799] Asynchronous scheduling is enabled.
INFO 04-20 20:13:14 [kernel.py:199] Final IR op priority after setting platform defaults: IrOpPriorityConfig(rms_norm=['native'])
(EngineCore pid=28132) INFO 04-20 20:13:21 [core.py:105] Initializing a V1 LLM engine (v0.19.0) with config: model='D:\\Resources\\Models\\Qwen2.5-7B-Instruct-AWQ', speculative_config=None, tokenizer='D:\\Resources\\Models\\Qwen2.5-7B-Instruct-AWQ', skip_tokenizer_init=False, tokenizer_mode=auto, revision=None, tokenizer_revision=None, trust_remote_code=True, dtype=torch.float16, max_seq_len=4096, download_dir=None, load_format=auto, tensor_parallel_size=1, pipeline_parallel_size=1, data_parallel_size=1, decode_context_parallel_size=1, dcp_comm_backend=ag_rs, disable_custom_all_reduce=False, quantization=awq_marlin, quantization_config=None, enforce_eager=False, enable_return_routed_experts=False, kv_cache_dtype=auto, device_config=cuda, structured_outputs_config=StructuredOutputsConfig(backend='auto', disable_any_whitespace=False, disable_additional_properties=False, reasoning_parser='', reasoning_parser_plugin='', enable_in_reasoning=False), observability_config=ObservabilityConfig(show_hidden_metrics_for_version=None, otlp_traces_endpoint=None, collect_detailed_traces=None, kv_cache_metrics=False, kv_cache_metrics_sample=0.01, cudagraph_metrics=False, enable_layerwise_nvtx_tracing=False, enable_mfu_metrics=False, enable_mm_processor_stats=False, enable_logging_iteration_details=False), seed=0, served_model_name=D:\Resources\Models\Qwen2.5-7B-Instruct-AWQ, enable_prefix_caching=True, enable_chunked_prefill=True, pooler_config=None, compilation_config={'mode': <CompilationMode.VLLM_COMPILE: 3>, 'debug_dump_path': None, 'cache_dir': '', 'compile_cache_save_format': 'binary', 'backend': 'inductor', 'custom_ops': ['none'], 'ir_enable_torch_wrap': True, 'splitting_ops': ['vllm::unified_attention', 'vllm::unified_attention_with_output', 'vllm::unified_mla_attention', 'vllm::unified_mla_attention_with_output', 'vllm::mamba_mixer2', 'vllm::mamba_mixer', 'vllm::short_conv', 'vllm::linear_attention', 'vllm::plamo2_mamba_mixer', 'vllm::gdn_attention_core', 'vllm::olmo_hybrid_gdn_full_forward', 'vllm::kda_attention', 'vllm::sparse_attn_indexer', 'vllm::rocm_aiter_sparse_attn_indexer', 'vllm::unified_kv_cache_update', 'vllm::unified_mla_kv_cache_update'], 'compile_mm_encoder': False, 'cudagraph_mm_encoder': False, 'encoder_cudagraph_token_budgets': [], 'encoder_cudagraph_max_images_per_batch': 0, 'compile_sizes': [], 'compile_ranges_endpoints': [2048], 'inductor_compile_config': {'enable_auto_functionalized_v2': False, 'size_asserts': False, 'alignment_asserts': False, 'scalar_asserts': False, 'combo_kernels': True, 'benchmark_combo_kernel': True}, 'inductor_passes': {}, 'cudagraph_mode': <CUDAGraphMode.FULL_AND_PIECEWISE: (2, 1)>, 'cudagraph_num_of_warmups': 1, 'cudagraph_capture_sizes': [1, 2, 4, 8], 'cudagraph_copy_inputs': False, 'cudagraph_specialize_lora': True, 'use_inductor_graph_partition': False, 'pass_config': {'fuse_norm_quant': False, 'fuse_act_quant': False, 'fuse_attn_quant': False, 'enable_sp': False, 'fuse_gemm_comms': False, 'fuse_allreduce_rms': False}, 'max_cudagraph_capture_size': 8, 'dynamic_shapes_config': {'type': <DynamicShapesType.BACKED: 'backed'>, 'evaluate_guards': False, 'assume_32_bit_indexing': False}, 'local_cache_dir': None, 'fast_moe_cold_start': False, 'static_all_moe_layers': []}, kernel_config=KernelConfig(ir_op_priority=IrOpPriorityConfig(rms_norm=['native']), enable_flashinfer_autotune=True, moe_backend='auto')
(EngineCore pid=28132) INFO 04-20 20:13:22 [parallel_state.py:1400] world_size=1 rank=0 local_rank=0 distributed_init_method=tcp://198.18.0.1:50175 backend=gloo
[W420 20:13:22.000000000 socket.cpp:764] [c10d] The client socket has failed to connect to [Auronya]:50175 (system error: 10049 - 在其上下文中，该请求的地址无效。).
(EngineCore pid=28132) INFO 04-20 20:13:22 [parallel_state.py:1712] rank 0 in world size 1 is assigned as DP rank 0, PP rank 0, PCP rank 0, TP rank 0, EP rank N/A, EPLB rank N/A
(EngineCore pid=28132) D:\Projects\Python\Aplus2-runModelInvLLM\.venv\Lib\site-packages\vllm\v1\sample\logits_processor\builtin.py:182: UserWarning: expandable_segments not supported on this platform (Triggered internally at C:\actions-runner\_work\pytorch\pytorch\pytorch\c10/cuda/CUDAAllocatorConfig.h:39.)
(EngineCore pid=28132)   self.neg_inf_tensor = torch.tensor(
(EngineCore pid=28132) INFO 04-20 20:13:22 [gpu_model_runner.py:4735] Starting to load model D:\Resources\Models\Qwen2.5-7B-Instruct-AWQ...
(EngineCore pid=28132) INFO 04-20 20:13:22 [awq_marlin.py:420] Using MarlinLinearKernel for AWQMarlinLinearMethod
(EngineCore pid=28132) INFO 04-20 20:13:23 [cuda.py:362] Using FLASH_ATTN attention backend out of potential backends: ['FLASH_ATTN', 'FLASHINFER', 'TRITON_ATTN', 'FLEX_ATTENTION'].
(EngineCore pid=28132) INFO 04-20 20:13:23 [flash_attn.py:622] Using FlashAttention version 2
Loading safetensors checkpoint shards:   0% Completed | 0/2 [00:00<?, ?it/s]
Loading safetensors checkpoint shards:  50% Completed | 1/2 [00:05<00:05,  5.41s/it]
Loading safetensors checkpoint shards: 100% Completed | 2/2 [00:07<00:00,  3.61s/it]
Loading safetensors checkpoint shards: 100% Completed | 2/2 [00:07<00:00,  3.88s/it]
(EngineCore pid=28132) 
(EngineCore pid=28132) INFO 04-20 20:13:32 [default_loader.py:384] Loading weights took 7.88 seconds
(EngineCore pid=28132) INFO 04-20 20:13:33 [gpu_model_runner.py:4820] Model loading took 5.2 GiB memory and 10.455804 seconds
(EngineCore pid=28132) INFO 04-20 20:13:39 [backends.py:1051] Using cache directory: C:\Users\CelestNya\.cache\vllm\torch_compile_cache\81cc9299aa\rank_0_0\backbone for vLLM's torch.compile
(EngineCore pid=28132) INFO 04-20 20:13:39 [backends.py:1111] Dynamo bytecode transform time: 5.55 s
(EngineCore pid=28132) INFO 04-20 20:13:43 [backends.py:372] Cache the graph of compile range (1, 2048) for later use
(EngineCore pid=28132) INFO 04-20 20:13:46 [backends.py:390] Compiling a graph for compile range (1, 2048) takes 7.21 s
(EngineCore pid=28132) INFO 04-20 20:13:49 [decorators.py:655] saved AOT compiled function to C:\Users\CelestNya\.cache\vllm\torch_compile_cache\torch_aot_compile\8aba059e7b41b3170f75e20961d95692032de175a3e8f077ab05cd19c993a654\rank_0_0\model
(EngineCore pid=28132) INFO 04-20 20:13:49 [monitor.py:48] torch.compile took 15.77 s in total
(EngineCore pid=28132) INFO 04-20 20:13:50 [monitor.py:76] Initial profiling/warmup run took 0.84 s
(EngineCore pid=28132) INFO 04-20 20:13:50 [kv_cache_utils.py:829] Overriding num_gpu_blocks=0 with num_gpu_blocks_override=8
(EngineCore pid=28132) INFO 04-20 20:13:50 [gpu_model_runner.py:5883] Profiling CUDA graph memory: PIECEWISE=4 (largest=8), FULL=3 (largest=4)
(EngineCore pid=28132) INFO 04-20 20:13:51 [gpu_model_runner.py:5962] Estimated CUDA graph memory: 0.05 GiB total
(EngineCore pid=28132) INFO 04-20 20:13:51 [gpu_worker.py:437] Available KV cache memory: 0.67 GiB
(EngineCore pid=28132) INFO 04-20 20:13:51 [gpu_worker.py:471] In v0.19, CUDA graph memory profiling will be enabled by default (VLLM_MEMORY_PROFILER_ESTIMATE_CUDAGRAPHS=1), which more accurately accounts for CUDA graph memory during KV cache allocation. To try it now, set VLLM_MEMORY_PROFILER_ESTIMATE_CUDAGRAPHS=1 and increase --gpu-memory-utilization from 0.7000 to 0.7051 to maintain the same effective KV cache size.
(EngineCore pid=28132) INFO 04-20 20:13:51 [kv_cache_utils.py:1319] GPU KV cache size: 12,624 tokens
(EngineCore pid=28132) INFO 04-20 20:13:51 [kv_cache_utils.py:1324] Maximum concurrency for 4,096 tokens per request: 3.08x
Capturing CUDA graphs (mixed prefill-decode, PIECEWISE): 100%|████████████████████████████████████████████████| 4/4 [00:00<00:00, 35.23it/s]
Capturing CUDA graphs (decode, FULL): 100%|███████████████████████████████████████████████████████████████████| 3/3 [00:00<00:00, 37.88it/s]
(EngineCore pid=28132) INFO 04-20 20:13:52 [gpu_model_runner.py:6053] Graph capturing finished in 1 secs, took 0.03 GiB
(EngineCore pid=28132) INFO 04-20 20:13:52 [gpu_worker.py:598] CUDA graph pool memory: 0.03 GiB (actual), 0.05 GiB (estimated), difference: 0.02 GiB (52.9%).
(EngineCore pid=28132) INFO 04-20 20:13:52 [core.py:283] init engine (profile, create kv cache, warmup model) took 19.13 seconds
(EngineCore pid=28132) INFO 04-20 20:13:53 [vllm.py:799] Asynchronous scheduling is enabled.
(EngineCore pid=28132) INFO 04-20 20:13:53 [kernel.py:199] Final IR op priority after setting platform defaults: IrOpPriorityConfig(rms_norm=['native'])
```

</details>

> You: 你好，你是什么模型

> Assistant: WARNING 04-20 20:15:40 [input_processor.py:235] Passing raw prompts to InputProcessor is deprecated and will be removed in v0.18. You should instead pass the outputs of Renderer.render_cmpl() or Renderer.render_chat().

```sh
我是通义千问模型，由阿里云开发。通义千问是一个通用的语言模型，旨在生成与给定文本上下文最相关和最自然的补全内容。我可以回答问题、提供信息、参与对话等。如果您有任何问题或需要帮助，欢迎随时告诉我！
```

> You: 看看实力，2347是不是质数

```sh
Assistant: 2347 是一个质数。要验证这一点，可以检查它是否能被小于其平方根的任何质数整除。2347 的平方根大约是 48.45，所以我们只需要检查它是否能被 2、3、5、7、11、13、17、19、23、29、31、37、41 和 43 等质数整除。经过检查，2347 不能被这些质数中的任何一个整除，因此 2347 是一个质数。
```

> You: 23457呢

```sh
Assistant: 23457 不是一个质数。我们可以检查它是否能被某些较小的质数整除。通过简单的检查可以发现：

23457 能被 3 整除，因为它的各位数字之和（2 + 3 + 4 + 5 + 7 = 21）能被 3 整除。因此，23457 不是质数。

具体来说，23457 ÷ 3 = 7819，所以 23457 可以分解为 3 和 7819 的乘积。因此，23457 不是一个质数。
```

> You: 23477呢

```sh
Assistant: 23477 是否是一个质数，可以通过检查它是否能被小于其平方根的质数整除来确定。23477 的平方根大约是 153.2，所以我们需要检查它是否能被 2、3、5、7、11、13、17、19、23、29、31、37、41、43、47、53、59、61、67、71、73、79、83、89、97、101、103、107、109、113、127、131、137、139 和 149 等质数整除。

经过检查，23477 不能被这些质数中的任何一个整除，因此 23477 是一个质数。

所以，23477 是一个质数。
```
