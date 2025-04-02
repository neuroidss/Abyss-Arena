# Abyss Arena

https://neuroidss.github.io/Abyss-Arena

![llm optionaly rules 3d game](https://github.com/neuroidss/Abyss-Arena/blob/main/Screencast_from_2025-04-02_01-31-12.gif?raw=true)

```
make all happen on arena so not able to fall out of border. and make artifact abilities to fight on arena, close range attack more powerful, long range attack less powerful. player body and soul should be processed on engine level same as other creatures, so to make ability later to add other players to make mmorpg. for llm disable mode maybe souls will have desire to see and then will have autoagreement from abyss to inhabitate nearest see ability artifact and then know where is move ability artifact and ask to use abyss ability to move get autoagreement and crawl slowly to nearest move ability artifact, and then look and move to get fight ability artifacts. on attack will be destroyed each artifact separately. when player found and assembly with tool_creation_tool ability artifact ask him for example to use whis new tool_creation_tool ability artifact by inventing new llm abyss tool which will be new artifact ability, and then when abyss will create artifact with this new ability player if found where this new artifact was created also could assemble with it and use its new artifact ability which player created.

make game, like made in abyss, where abyss creates artifacts and creatures, depends on truth of desires and balancing values around it can be blessed or cursed, with which user can interact, where llm controlling 3d world and responding to interaction with user avatar which also consists of artifacts, so llm playing with user. first make multiple artifacts and one artifact which rewrites abyss laws by using its ability tool_creation_tool, users goal is to find it and assemble with it. create user inhabitated assembled artifacts one that gives ability to move and another gives ability to see what around. continue of game process is in infinite creation these artifacts and assemble nearest artifacts by inhabitating by previously absorbed by abyss souls of creatures or user when these creature souls was absorbed by abyss somewhere else, when soul absorbed by abyss from previous artifacts then artifacts disassembled and soul ruled by abyss moved to search other prefered artifacts if they fits souls desire. abyss is greedy, what created by abyss will return back, means all tends to disassemble. users soul desire is to rewrite laws of abyss, like tool creation tool, which able to disassemble and reassemble anything if user will learn how to use it, and so users soul will inhabihate in artifacts which rewrite abyss laws if found it. add some souls around which will inhabitate some artifacts. possibility to disassembly will become after time lets say expiration time five minutes from artifact creation, then abyss will be asked need to disassemble this artifact if it was not used as desired, like if player will not move for expiration time its moving artifact may be disassembled, or if will not look around for expiration time then sensing artifact may be disassembled if abyss decided so, but any way user better find new artifacts that not expired. expiration can be delayed by proper usage and by finding similar artifacts to assembly will lead to upgrade ability. abyss creates artifacts infinitely in cycle. artifacts gives abilities when inhabitates with soul. abyss llm potentially can create new artifact abilities via tool_creation_tool, which can later be called via llm abyss call or directly via use artifact by creature or player. all llm tools are abilities of artifacts which can be used by abyss itself or called by soul with inhabitable artifact with such ability. from chat user have access only to tools abilities from artifacts which was collected and assembled. initially player moves only via his artifact llm tool ability to move, same see what around he can only via artifact ability to see, if he loose these artifacts he will not be able to move and see. game for llm should be in continuous messages context with ability of interaction with user in chat but not pause game process, optimize context when it is too big depends on performance of llm. put messages on top side of screen to not interfere with controls on touchscreen. use infinite agent thinking step by step process, every step must use tools calling. make agent be able to schedule future actions to make its actions smoother, less dependent on llm request delay. make ability to add dynamically multiple llm calls from multiple llm engines in parallel and plan for one-two seconds of actions or other measured time required in one llm call before next llm call, to make even smoother. all inworld elements must be somehow interactable. don't invent fake moves when llm error, try again until correct llm response. make keyboard&mouse, real gamepad and multitouch onscreen gamepad joysticks controls for 3d move and 3d rotate, should be desktop and mobile ready. make sure not using browser alert() popups. add some sounds, but without external sound resources. Add a physics engine rapier for more realistic movement and collisions, but only that function you sure exists in current version. use threejs >=0.140.0. use nipplejs. import from esm.run inside <script type="module">.
import * as THREE from 'https://esm.run/three@0.160.0';
import nipplejs from 'https://esm.run/nipplejs@0.10.1';
use new nipplejs.create()

include 2025 Vibe Coding Game Jam participation note:
<a target="_blank" href="https://jam.pieter.com" style="font-family: 'system-ui', sans-serif; position: fixed; bottom: -1px; right: -1px; padding: 7px; font-size: 14px; font-weight: bold; background: #fff; color: #000; text-decoration: none; z-index: 10; border-top-left-radius: 12px; z-index: 10000; border: 1px solid #fff;"> Vibe Jam 2025</a>

this is for jam so only include most playable featured but fully implement them all. as by jam rules game must be fully playable instantly without loading screen, then for faster test, some content should be precreated by some world creation starting script which will like emulate abyss tool calls for artifact creation, and turn on/of/switch llm ability should be optional. so do not delay any how gameplay by llm existence. llm should only add additional features when enabled, and should be easy disabled/reanabled/switched without interruption or pause for gameplay. make user guarantee to have at start movement and vision artifacts. for DeepSeek-R1 versions maybe make them generate custom tool request immediately after tag <think></think>. make some circles of abyss, zero level is near arena circle diameter where just artifacts without enemy creatures, cloder to center creatures becones more agressive, faster, with more powerful artifacts. add llm chat with custom tool calling, as native tool calling not yet supported in webllm for qwen.
make guaranteed precreated some enemies with different artifact abilities, for player to fight while he searching tool_creation_tool ability artifact, so if he will not found how to fight then using artifacts around then he will not survive to find his main goal. game can be played from start to end without llm except last quest when player should learn how to use achieved artifact with tool_creation_tool ability to finally rewrite abyss rules, it can't be done without llm enabled, but player will be ready for deal in abyss to this moment. make each level large enough for player to take some time to move through it fighting with enemies and collecting artifacts.

to use web-llm.
<script type="module">
import * as webllm from "https://esm.run/@mlc-ai/web-llm";
llmEngine = await webllm.CreateMLCEngine(
"Qwen2.5-Coder-7B-Instruct-q4f32_1-MLC",
{ initProgressCallback: reportProgress }
);
don't use appConfig.
with reportProgress use progress.progress if needed.
use engine.chat.completions.create but without its native tools feature, instead use custom tools, stream: false, also set temperature in it.
make ability to switch between Qwen2.5-Coder-7B-Instruct-q4f32_1-MLC and Qwen2.5-Coder-3B-Instruct-q4f32_1-MLC, DeepSeek-R1-Distill-Qwen-7B-q4f32_1-MLC, and set temperature of generation. make ability to choose qwen model size before load any of it.
DeepSeek-R1 has tag <think></think> at start.

add ability to use llm.js for who not have webgpu.
add ability to use external apis openai, gemini, claude, ollama or other when you know how to add them for who not have local powerful hardware.

add in llm tools list for chatbot llm tool_creation_tool with parameters 'name' and 'description' and which calls engine chat create to create js function which makes what in 'description' and named as 'name', and evaluates this new js function, then creates llm tool with same name and description and parameters which was used in new created js function, and adding new llm tool in available llm tools list for chatbot, js function should take a single parameters object as named array. for tools declaration use assistant prompt but place it each time before new user message in history, but don't keep this tools usage message in history as it will be always updated. for created tools js functions and json parameters use only code inside blocks ```javascript ```, ```json ```, remove these block markers. if using, json block for tools use detection then remove ```json ``` block markers before parsing.

don't use role 'system', instead place info every time before last user message but don't include in history. don't use role tool, last message to llm must be from role user.

initialize after all elements created. make comments in console.log. separate in log what for with llm mode and without llm mode.

for llm.js:
use one of
https://huggingface.co/unsloth/Qwen2.5-Coder-3B-Instruct-128K-GGUF/resolve/main/Qwen2.5-Coder-3B-Instruct-Q4_K_M.gguf
https://huggingface.co/unsloth/Qwen2.5-Coder-7B-Instruct-128K-GGUF/resolve/main/Qwen2.5-Coder-7B-Instruct-Q4_K_M.gguf
https://huggingface.co/unsloth/Qwen2.5-Coder-14B-Instruct-128K-GGUF/resolve/main/Qwen2.5-Coder-14B-Instruct-Q4_K_M.gguf
https://huggingface.co/unsloth/DeepSeek-R1-Distill-Qwen-1.5B-GGUF/resolve/main/DeepSeek-R1-Distill-Qwen-1.5B-Q4_K_M.gguf
https://huggingface.co/unsloth/DeepSeek-R1-Distill-Qwen-7B-GGUF/resolve/main/DeepSeek-R1-Distill-Qwen-7B-Q4_K_M.gguf
https://huggingface.co/unsloth/DeepSeek-R1-Distill-Qwen-14B-GGUF/resolve/main/DeepSeek-R1-Distill-Qwen-14B-Q4_K_M.gguf
with llm.js qwen2.5 use ChatML template
import exact "./llm.js/llm.js", it is on local server location
it is from https://github.com/rahuldshetty/llm.js
DeepSeek-R1 has tag <think></think> at start, and <｜User｜> and <｜Assistant｜> tokens chat template formatter.

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
