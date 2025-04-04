# Abyss Arena

https://neuroidss.github.io/Abyss-Arena

![llm optionaly rules 3d game](https://github.com/neuroidss/Abyss-Arena/blob/main/Screencast_from_2025-04-02_01-31-12.gif?raw=true)

```
init abyss llm before world init. game world initialization may be abyss llm tool, but at first time world init should be with default parameters so just run this llm tool, but later abyss llm could reinit world with its parameters. this is why abyss have tool to sense world, as it have tool to create world. so also give to abyss tools to recreate world.

first generate detailed strategic plan, and next make full code of all features implementation in single html block.
remove maximum comments from code, make code selfcommented, so no needs comments.

make keyboard wasd for 3d move & mouse movement for 3d look, real gamepad and multitouch onscreen gamepad joysticks controls left for 3d move and right for 3d move, should be desktop and mobile ready. make sure not using browser alert() popups.

import these libraries at start directly after <script type="module">:
import {LLM} from "./llm.js/llm.js";
import * as webllm from "https://esm.run/@mlc-ai/web-llm";
import * as RAPIER from "https://esm.run/@dimforge/rapier3d-compat@0.12.0";
import * as THREE from "https://esm.run/three@0.160.0";
import nipplejs from "https://esm.run/nipplejs@0.10.1";

import exact path "./llm.js/llm.js", as it is on local server location extracted from https://github.com/rahuldshetty/llm.js/releases/download/2.0.1/llm.js-2.0.1.zip

await RAPIER.init(); 
use new nipplejs.create()

llmEngine_webllm = await webllm.CreateMLCEngine(
"Qwen2.5-Coder-3B-Instruct-q4f32_1-MLC",
{ initProgressCallback: reportProgress }
);
don't use appConfig.
with reportProgress use progress.progress if needed.
use engine.chat.completions.create but without its native tools feature, instead use custom tools, stream: false, also set temperature in it.
use response.choices[0].message.content to get first response text.
make ability to switch between "Qwen2.5-Coder-7B-Instruct-q4f32_1-MLC" and "Qwen2.5-Coder-3B-Instruct-q4f32_1-MLC", "DeepSeek-R1-Distill-Qwen-7B-q4f32_1-MLC", and set temperature of generation. make ability to choose qwen model size before load any of it.

add ability to choose use llm.js for who not have webgpu.

add in llm tools list for chatbot llm tool_creation_tool with parameters 'name' and 'description' and which calls engine chat create to create js function which makes what in 'description' and named as 'name', and evaluates this new js function, then creates llm tool with same name and description and parameters which was used in new created js function, and adding new llm tool in available llm tools list for chatbot, js function should take a single parameters object as named array. for tools declaration use assistant prompt but place it each time before new user message in history, but don't keep this tools usage message in history as it will be always updated. for created tools js functions and json parameters use only code inside blocks ```javascript ```, ```json ```, remove these block markers. if using, json block for tools use detection then remove ```json ``` block markers before parsing.

inside tool_creation_tool provide tool parameters example in prompt to llm which creates new javascript function and which returns function parameters json block:
      {
          'name': 'tool_name',
          'description': 'tool description',
          'parameters': {
            'type': 'object',
            'properties': {
              'first_parameter_name': {
                'type': 'string',
                'description': 'first parameter description',
              },
              'second_parameter_name': {
                'type': 'string',
                'description': 'second parameter description',
              },
            },
            'required': ['first_parameter_name', 'second_parameter_name'],
          },
      };

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
with llm.js qwen2.5 use ChatML template.
don't forget to include smallest available DeepSeek-R1-Distill-Qwen-1.5B, it is only available in llm.js, not in webllm, so make correct ability to choose between webllm and llm.js.
DeepSeek-R1 has <｜User｜> and <｜Assistant｜> tokens chat template formatter.

here example of llm.js Quick Start:

// Import LLM app
import {LLM} from "./llm.js/llm.js";

// State variable to track model load status
var model_loaded = false;

// Initial Prompt
var initial_prompt = "create tool for artifact ability to melee_attack";

// Callback functions
const on_loaded = () => { model_loaded = true; };
const write_result = (text) => { document.getElementById('result').innerText += text + "\n" };
const run_complete = () => {};

// Configure LLM app
const llmEngine_llmjs = new LLM(
  // Type of Model
  'GGUF_CPU',

  // Model URL
  'https://huggingface.co/unsloth/DeepSeek-R1-Distill-Qwen-1.5B-GGUF/resolve/main/DeepSeek-R1-Distill-Qwen-1.5B-Q4_K_M.gguf',

  // Model Load callback function
  on_loaded,

  // Model Result callback function
  write_result,

  // On Model completion callback function
  run_complete
);

// Download & Load Model GGML bin file
llmEngine_llmjs.load_worker();

// Trigger model once its loaded
const checkInterval = setInterval(timer, 5000);

function timer() {
  if(model_loaded){
    llmEngine_llmjs.run({
      prompt: initial_prompt,
      top_k: 1
    });
    clearInterval(checkInterval);
  } else {
    console.log('Waiting...');
  }
}


game must be fully playable instantly without loading screen, then for faster test, and turn on/of/switch llm ability should be optional. so do not delay any how gameplay by llm existence. llm should only add additional features when enabled, and should be easy disabled/reanabled/switched without interruption or pause for gameplay.
llm when enable should start custom calling tool tool_creation_tool for new artifact abilities, and then start calling tool create_artifact with these newly created artifact abilities. then player should find these newly created artifacts and get and use these new abilities. game for llm should be in continuous messages context with ability of interaction with user in chat but not pause game process, optimize context when it is too big depends on performance of llm. put messages on top side of screen to not interfere with controls on touchscreen, and make autoscrolling to latest message. use infinite agent thinking step by step process, every step must end with custom tools calling. make agent be able to schedule future actions to make its actions smoother, less dependent on llm request delay. create one artifact or artifact ability at one custom tool call, depends on what abyss see in game world each step. give to abyss llm suggestion which artifact abilities to create and which artifact to create with these new abilities, with exact custom tool call prompts to do it. artifact when equipped and used -- calling abyss llm custom tool call with its artifact ability.

add to abyss llm example of how to create new ability for artifact, and next how to create artifact in world map with this new ability for player to equip and use. so, llm can create artifacts with any new created and existed artifact abilities, all llm tools are artifact abilities.
no need to create separate artifact abilities array, use same array as llm tools, artifact can be created from any llm tool as they are abyss abilities which granted to artifacts to call by artifact owner and can be called by abyss too as just tool call. provide abyss llm with hints which entities exists in game engine with which llm can operate in created artifact abilities. give abyss llm tool create_artifact.

make arena and so no one will fall out of this arena boundaries. but make this arena boundaries don't interfere camera view.

don't use native tools in chat.completions.create({tools}) as native tool calling is unaccessible for qwen and deepseek models, use provided in example custom tool calling. make loaded model variable global.
add variant to choose between llm.js and webgpu. menu options to choose model should not interfere with llm message window.
use custom realization of tool calls for both llm.js and webgpu.

place precreated artifacts in world map with precreated tools abilities where used entities of game engine, so abyss llm could create artifacts with same and new artifact abilities when wishes to. make possibility for user to collect these artifacts, and make dynamic user interface for player to use collected artifacts, when user pick artifact then map its ability to some keys and buttons and onscreen for multitouch. an base of abyss llm tools tool_creation_tool and create_artifact are also can be created artifacts and these artifact abilities then can be used by player. if not sure how to use artifact ability then make abyss llm decide what happen when artifact ability called.

log all llm interactions to console.log. don't overload llm with incoming messages from world, make it get needed info on its own frequency as it is local llm and can have big time for processing of users hardware. maybe make special tool to look around so abyss llm can call it sense state of abyss, as user do looking. or send abyss sensing data to abyss llm each time asking it to do something like create new artifact abilities or new artifacts.

first generate detailed strategic plan, and next make full code of all features implementation in single html block.

make keyboard wasd for move & mouse movement for look, real gamepad and multitouch onscreen gamepad controls left joystick for move and right joystick for look, should be desktop and mobile ready.

in planning stage describe in details how abyss will get info about game state, how to use tool calls, how will be organized creation of new artifact abilities via tool calls and creation of new artifacts and adding artifact abilities to player when he collect artifacts and how user will use these artifact abilities. make plan how you will tell to abyss llm how to call tools and which tools it has. plan how you tell to abyss how it can get info about game engine entities how to make new artifact abilities with them.

make llm tool to get game entities available in scope. for info how to create new artifact abilities. it is more detailed than just world map, as it is for engineering purposes. or maybe insert more detailed engineering info into sense tool. any way llm needs to know which game entities and how to use to create new artifact abilities. maybe create as many as possible artifact abilities, and make llm ability to get code of these tools, so llm colud use these tools as examples for new tools.

give to abyss llm tool to recreate world, and if abyss llm will decide it can spawn this artifact with such ability. only create artifacts with existing abyss llm tools as artifact abilities. 

collected artifact should be attached to players avatar, and when use this artifact -- use its ability as abyss llm tool.

there no setEnabledRotations functiion in rapier3d, use something else.

create artifact abilities for different element systems, to create artifacts with them.
create different creatures which will live in world among player attached to these element systems when they got these artifacts and become affected by attacks from opposite element from element system. creature can take only artifacts which fits creature element. player can take any element artifacts.

make also melee close range small, melee close range middle, melee close range big, melee long range, catalist weapon types of each element.
here elemental resonance pyro with hydro vaporize, with electro over-load, with cryo melt, with dendro burning, with anemo swirl, with geo crystalyze, hydro with electro electro-charged, with cryo frozen, with dendro bloom with pyro burgeon with electro hyper-bloom, with anemo swirl, with geo crystalyze, electro with cryo super-conduct, with dendro quicken spread aggravate, cryo with wind swirl, with geo crystalyze.
make creatures by different families.
make creatures by types Common Enemies, Elite Enemies, Normal Bosses, Weekly Bosses. stronger creature types are less in number on floor, but as higher floor as stronger creature types.
make abyss spiral 12 floors with 3 subfloors on each floor, so enemy power increases floor by floor. when player defeated all creatures on current floor recreate next floor, if player defeated recreate to first subfloor of current floor, so player need to defeat three subfloors to get to next floor. when defeated all floor and subfloors will show shareable results of all floors and subfloors battles, and then player can repeat from any floor to get better results on each floor to share, floor result changed only when all subfloors finished.
if player or creature acidentally fall away of fly too high from arena then it looses.
before each floor starts, user have time to choose weapons with which will fight three subfloors. enemies will spawn with equipped weapons.
```

