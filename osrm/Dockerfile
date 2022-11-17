FROM osrm/osrm-backend

ARG PROFILE
RUN echo $PROFILE

RUN mkdir -p /data
RUN apt-get update && apt-get install -y wget
RUN wget -O /data/quebec-latest.osm.pbf https://download.geofabrik.de/north-america/canada/quebec-latest.osm.pbf

RUN /usr/local/bin/osrm-extract -p $PROFILE /data/quebec-latest.osm.pbf
RUN /usr/local/bin/osrm-partition /data/quebec-latest.osrm
RUN /usr/local/bin/osrm-customize /data/quebec-latest.osrm
# RUN /usr/local/bin/osrm-contract mtl.osrm
RUN rm /data/quebec-latest.osm.pbf

EXPOSE 5000

CMD /usr/local/bin/osrm-routed --max-table-size 8000 --max-matching-size 1000 --algorithm mld /data/quebec-latest.osrm
