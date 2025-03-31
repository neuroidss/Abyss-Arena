# Abyss-Game---LLM-Controlled-World

https://neuroidss.github.io/Abyss-Game---LLM-Controlled-World

```
make game, like made in abyss, where abyss creates artifacts and creatures, depends on truth of desires and balancing values around it can be blessed or cursed, with which user can interact, where llm controlling 3d world and responding to interaction with user avatar which also consists of artifacts, so llm playing with user. first make multiple controversial memes artifacts and one artifact which rewrites abyss laws and near one of these artifacts add users soul captured by abyss earlier. continue of game process is in infinite creation these controversial memes artifacts and assemble nearest artifacts by inhabitating by previously absorbed souls of creatures or user when these creature souls was absorbed by abyss somewhere else, when soul absorbed from previous artifacts then artifacts disassembled and soul ruled by abyss moved to search other prefered artifacts if they fits souls desire. abyss is greedy, what created by abyss will return back, means all tends to disassemble. controversial memes means what llm found controversial in current abyss state. users soul desire is to rewrite laws of abyss, like tool creation tool, which able to disassemble and reassemble anything if user will learn how to use it, and so users soul will inhabihate in artifacts which rewrite abyss laws. add some souls around which will inhabitate some artifacts. disallembly time lets say after minute from artifact creation. abyss creates artifacts infinitely in cycle. game for llm should be in continuous messages context with ability of interaction with user in chat but not pause game process, optimize context when it is too big depends on performance of llm. put messages on top side of screen to not interfere with controls on touchscreen which in middle of screen. use infinite agent thinking step by step process, every step must use tools calling. make agent be able to schedule future actions to make its actions smoother, less dependent on llm request delay. make ability to add dynamically multiple llm calls from multiple llm engines in parallel and plan for one-two seconds of actions or other measured time required in one llm call before next llm call, to make even smoother. all inworld elements must be somehow interactable. don't invent fake moves when llm error, try again until correct llm response. make keyboard&mouse, real gamepad and multitouch onscreen gamepad joysticks controls for 3d move and 3d rotate, should be desktop and mobile ready. make sure not using browser alert() popups. add some sounds, but without external sound resources. Add a physics engine (like Rapier.js or Cannon-es) for more realistic movement and collisions, but only that function you sure exists in current version. use threejs >=0.140.0. use nipplejs. import from cdn or esm.run inside <script type="module">. if using rapier then use just 'capsule', not 'capsuleY'.

include 2025 Vibe Coding Game Jam participation note:
<a target="_blank" href="https://jam.pieter.com" style="font-family: 'system-ui', sans-serif; position: fixed; bottom: -1px; right: -1px; padding: 7px; font-size: 14px; font-weight: bold; background: #fff; color: #000; text-decoration: none; z-index: 10; border-top-left-radius: 12px; z-index: 10000; border: 1px solid #fff;"> Vibe Jam 2025</a>

add llm chat with custom tool calling, as native tool calling not yet supported in webllm for qwen.
to use web-llm.

<script type="module">
import * as webllm from "https://esm.run/@mlc-ai/web-llm";
llmEngine = await webllm.CreateMLCEngine(
"Qwen2.5-Coder-7B-Instruct-q4f32_1-MLC",
{ initProgressCallback: reportProgress }
);
don't use appConfig.
with reportProgress use progress.progress if needed.
use engine.chat.completions.create but without its native tools feature, indtead use custom tools, stream: false, also set temperature in it.
make ability to switch between Qwen2.5-Coder-7B-Instruct-q4f32_1-MLC and Qwen2.5-Coder-3B-Instruct-q4f32_1-MLC, and set temperature of generation. make ability to choose qwen model size before load any of it.

add ability to use llm.js for who not have webgpu.
add ability to use external apis openai, gemini, claude, ollama or other when you know how to add them for who not have local powerful hardware. 

add in llm tools list for chatbot llm tool_creation_tool with parameters 'name' and 'description' and which calls engine chat create to create js function which makes what in 'description' and named as 'name', and evaluates this new js function, then creates llm tool with same name and description and parameters which was used in new created js function, and adding new llm tool in available llm tools list for chatbot, js function should take a single parameters object as named array. for tools declaration use assistant prompt but place it each time before new user message in history, but don't keep this tools usage message in history as it will be always updated. for created tools js functions and json parameters use only code inside blocks ```javascript ```, ```json ```, remove these block markers. if using, json block for tools use detection then remove ```json ``` block markers before parsing.

don't use role 'system', instead place info every time before last user message but don't include in history. don't use role tool, last message to llm must be from role user.

initialize after all elements created. make comments in console.log.

for llm.js:
use one of
https://huggingface.co/unsloth/Qwen2.5-Coder-3B-Instruct-128K-GGUF/resolve/main/Qwen2.5-Coder-3B-Instruct-Q4_K_M.gguf
https://huggingface.co/unsloth/Qwen2.5-Coder-7B-Instruct-128K-GGUF/resolve/main/Qwen2.5-Coder-7B-Instruct-Q4_K_M.gguf
https://huggingface.co/unsloth/Qwen2.5-Coder-14B-Instruct-128K-GGUF/resolve/main/Qwen2.5-Coder-14B-Instruct-Q4_K_M.gguf
with llm.js qwen2.5 use ChatML template
import exact "./llm.js/llm.js", it is on local server location
it is from https://github.com/rahuldshetty/llm.js

here example of Quick Start:
// Import LLM app
import {LLM} from "./llm.js/llm.js";

// State variable to track model load status
var model_loaded = false;

// Initial Prompt
var initial_prompt = "def fibonacci(n):"

// Callback functions
const on_loaded = () => {
model_loaded = true;
}
const write_result = (text) => { document.getElementById('result').innerText += text + "\n" }
const run_complete = () => {}

// Configure LLM app
const llmEngine = new LLM(
// Type of Model
'GGUF_CPU',

// Model URL
'https://huggingface.co/RichardErkhov/bigcode_-_tiny_starcoder_py-gguf/resolve/main/tiny_starcoder_py.Q8_0.gguf',

// Model Load callback function
on_loaded,

// Model Result callback function
write_result,

// On Model completion callback function
run_complete
);

// Download & Load Model GGML bin file
llmEngine.load_worker();

// Trigger model once its loaded
const checkInterval = setInterval(timer, 5000);

function timer() {
if(model_loaded){
llmEngine.run({
prompt: initial_prompt,
top_k: 1
});
clearInterval(checkInterval);
} else{
console.log('Waiting...')
}
}
```
