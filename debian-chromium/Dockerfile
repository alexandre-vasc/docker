FROM debian:unstable
SHELL ["/bin/bash", "-c"]

RUN sed -i '0,/RE/s/main/main contrib non-free/' /etc/apt/sources.list
RUN printf 'path-exclude=/usr/share/locale/*\npath-exclude=/usr/share/doc/*\npath-include=/usr/share/locale/en/*' > /etc/dpkg/dpkg.cfg.d/purge
RUN apt-get update && apt-get install -yq --no-install-recommends \
    chromium libgl1-mesa-dri libcanberra-gtk-module libexif-dev pepperflashplugin-nonfree pulseaudio \
    && rm -rf /tmp/* /var/{tmp,cache}/* /var/lib/{apt,dpkg}/

RUN adduser --disabled-password user --gecos "User"
USER user
ENV HOME /home/user
ENV PULSE_SERVER unix:/tmp/pulse

CMD ["chromium","--no-sandbox","--no-first-run","about:blank"]
