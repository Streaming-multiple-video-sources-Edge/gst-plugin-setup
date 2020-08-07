FROM docker.io/jweng1/gst-base-img:v1

COPY . /apptest
WORKDIR /apptest

RUN git clone https://github.com/Streaming-multiple-video-sources-Edge/GST-plugin.git && cd GST-plugin 

RUN python3 -m venv venv

RUN apt update && apt install python3-pip -y

RUN . ./venv/bin/activate && pip3 install -U wheel pip setuptools && pip3 install -r GST-plugin/requirements.txt

RUN . ./venv/bin/activate && export GST_PLUGIN_PATH=$GST_PLUGIN_PATH:/apptest/venv/lib/gstreamer-1.0/:/apptest/GST-plugin/gst/ && gst-inspect-1.0 python

CMD . ./venv/bin/activate && export GST_PLUGIN_PATH=$GST_PLUGIN_PATH:/apptest/venv/lib/gstreamer-1.0/:/apptest/GST-plugin/gst/ && exec python3 GST-plugin/parse_files/parse1.py
