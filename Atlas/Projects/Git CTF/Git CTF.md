

## Intuition

Git CTF is a Docker image where users can practice git with scenarios

So a Docker Image with base light weight ubuntu , git , vim
inside that  a generator which generates git commands based in json format of git setup given by AI

commands such as 

`gitctf config APIKEY` used to give api key
`gitctf config TYPE` used to give ai type , if gemini then we can send in its format etc for this may be we will keep a json file like 

```
type:'gemini'
format:''
```
format is how we send request to that AI
so that use manually can add his own type

`gitctf config APIURL` url to send request to

`gitctf setup --format state.json` internally used to generate the setup

`gitctf new-scenario` creates a new scenario and shows output like
```
new task created at /plays/play1

`displays readme file`
```

readme file created by AI to explain the setup, scenario and task and expected output

```
git validate play1
```

this would send AI the whole context before and after what user did, the file content etc , it validates everything
and in json might be like

```
assert:true
advices:"text advice"
```

```
assert:false
advices:"text advice"
```



