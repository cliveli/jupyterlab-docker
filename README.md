# Jupyterlab Docker

📙 JupyterLab + NodeV10 / Py2 / Py3 kernels + Container 🐳 = Awesome Learning Tools 👩‍💻👨‍💻

<br/>
<br/>

![demo-1][demo-1]

## Run Online in [_Play With Docker_][pwd-link] (free)

1. Click [![Try in PWD][try-pwd-img]][try-pwd-link] to launch a new container. After the stack builder is finished, close the dialog.

  - ![pwd-run-1][pwd-run-1]

2. Get Access Token by running this command in the terminal prompt:

  ```sh
  docker logs $(docker container list | awk 'FNR==2{print $1}') 2>&1 \
    | grep -E 'token=(.*)' -o | cut -c7-54
  ```

3. Click the link above to access Jupyter page:

  - ![pwd-run-2][pwd-run-2]

4. In page paste the token in the input field to login

  - ![pwd-run-3][pwd-run-3]

5. 🎉 Congrats! Now you can create a Notebook with JavaScript, Python 3 or Python 2 Environment!

  - ![pwd-run-4][demo-1]

## Run in Your Local Machine

1. Run Following command in your terminal:

  ```bash
  docker run -d -p 8888:8888 liuderchi/jupyterlab-ijavascript:latest
  ```

2. Run following command to get Jupyter token. Then Copy it.

  ```bash
  docker logs $(docker container list | awk 'FNR==2{print $1}') 2>&1 \
      | grep -E 'token=(.*)' -o | cut -c7-54
  ```

3. In browser go to `localhost:8888?token=PASTE_JUPYTER_TOKEN_HERE`


## Run and Save Custom Settings

```bash
$ git clone https://github.com/liuderchi/jupyterlab-docker.git
$ cd jupyterlab-docker/jupyterlab
$ docker run -d -p 8888:8888 \
  -v $PWD/jupyterlab-settings:/root/.jupyter/lab/user-settings/@jupyterlab \
  liuderchi/jupyterlab-ijavascript:latest

# print jupyter token
$ docker logs $(docker container list | awk 'FNR==2{print $1}') 2>&1 \
  | grep -E 'token=(.*)' -o | cut -c7-54
```

in browser go to `localhost:8888?token=PASTE_JUPYTER_TOKEN_HERE`

Now you can enjoy jupyterlab and save custom settings in your disk (_Menu Bar > Settings > Advanced Settings Editor_). \
Setting files will be saved in `jupyterlab/jupyterlab-settings`.

## Inspiration

This project is a fork from [mikebirdgeneau/jupyterlab-docker][mikebirdgeneau/jupyterlab-docker]

## License

[MIT License][mit-license]

[demo-1]: https://user-images.githubusercontent.com/4994705/44621173-e8142400-a8d3-11e8-9d1f-01abc34e3064.png
[pwd-link]: https://labs.play-with-docker.com/
[try-pwd-img]: https://cdn.rawgit.com/play-with-docker/stacks/cff22438/assets/images/button.png
[try-pwd-link]: http://play-with-docker.com?stack=https://raw.githubusercontent.com/liuderchi/jupyterlab-docker/master/stack.yml
[pwd-run-1]: https://user-images.githubusercontent.com/4994705/44618078-d87be780-a8a1-11e8-9226-7f36616f90cc.png
[pwd-run-2]: https://user-images.githubusercontent.com/4994705/42303031-6e6cbebe-8051-11e8-8dea-928481c0f4e4.png
[pwd-run-3]: https://user-images.githubusercontent.com/4994705/44618015-c51c4c80-a8a0-11e8-903a-5627ee53a153.png
[mikebirdgeneau/jupyterlab-docker]: https://github.com/mikebirdgeneau/jupyterlab-docker
[mit-license]: https://liuderchi.mit-license.org/ 'mit-license'
