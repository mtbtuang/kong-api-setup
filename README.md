# kong-api-setup

docker network create webproxy
docker network create kong_network

docker exec -it "container id" sh
apk add postgresql-client
psql -h 127.0.0.1 -U kong -d konga -p 5432

DROP TABLE IF EXISTS public.konga_users;

CREATE TABLE public.konga_users (
   id SERIAL PRIMARY KEY,
   username VARCHAR(255) NOT NULL,
   email VARCHAR(255) NOT NULL,
   password VARCHAR(255) NOT NULL,
   first_name VARCHAR(255),
   last_name VARCHAR(255),
   reset_password_token VARCHAR(255),
   confirmed BOOLEAN DEFAULT false,
   blocked BOOLEAN DEFAULT false,
   created_at TIMESTAMPTZ DEFAULT now(),
   updated_at TIMESTAMPTZ DEFAULT now()
);
 
\q
exit
docker restart "container id"



