--
-- PostgreSQL database dump
--

-- Dumped from database version 12.17 (Ubuntu 12.17-1.pgdg22.04+1)
-- Dumped by pg_dump version 12.17 (Ubuntu 12.17-1.pgdg22.04+1)

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

DROP DATABASE universe;
--
-- Name: universe; Type: DATABASE; Schema: -; Owner: freecodecamp
--

CREATE DATABASE universe WITH TEMPLATE = template0 ENCODING = 'UTF8' LC_COLLATE = 'C.UTF-8' LC_CTYPE = 'C.UTF-8';


ALTER DATABASE universe OWNER TO freecodecamp;

\connect universe

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

SET default_tablespace = '';

SET default_table_access_method = heap;

--
-- Name: galaxy; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.galaxy (
    galaxy_id integer NOT NULL,
    name character varying(40) NOT NULL,
    description text,
    has_stars boolean DEFAULT false,
    size_across_in_million_light_years numeric(6,3),
    distance_to_earth_in_light_years integer
);


ALTER TABLE public.galaxy OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.galaxy_galaxy_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.galaxy_galaxy_id_seq OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.galaxy_galaxy_id_seq OWNED BY public.galaxy.galaxy_id;


--
-- Name: moon; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.moon (
    moon_id integer NOT NULL,
    planet_id integer NOT NULL,
    name character varying(40) NOT NULL,
    description text,
    is_spherical boolean,
    distance_from_planet_in_km integer
);


ALTER TABLE public.moon OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.moon_moon_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.moon_moon_id_seq OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.moon_moon_id_seq OWNED BY public.moon.moon_id;


--
-- Name: planet; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.planet (
    planet_id integer NOT NULL,
    star_id integer NOT NULL,
    name character varying(40) NOT NULL,
    description text,
    has_moons boolean DEFAULT false,
    distance_to_star_in_million_kms numeric(10,3)
);


ALTER TABLE public.planet OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.planet_planet_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.planet_planet_id_seq OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.planet_planet_id_seq OWNED BY public.planet.planet_id;


--
-- Name: solar_system; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.solar_system (
    solar_system_id integer NOT NULL,
    name character varying(40) NOT NULL,
    star_id integer NOT NULL,
    planet_id integer NOT NULL
);


ALTER TABLE public.solar_system OWNER TO freecodecamp;

--
-- Name: solar_system_solar_system_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.solar_system_solar_system_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.solar_system_solar_system_id_seq OWNER TO freecodecamp;

--
-- Name: solar_system_solar_system_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.solar_system_solar_system_id_seq OWNED BY public.solar_system.solar_system_id;


--
-- Name: star; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.star (
    star_id integer NOT NULL,
    galaxy_id integer NOT NULL,
    name character varying(40) NOT NULL,
    description text,
    has_planets boolean DEFAULT false,
    age_in_million_years numeric(10,3)
);


ALTER TABLE public.star OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.star_star_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.star_star_id_seq OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.star_star_id_seq OWNED BY public.star.star_id;


--
-- Name: galaxy galaxy_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy ALTER COLUMN galaxy_id SET DEFAULT nextval('public.galaxy_galaxy_id_seq'::regclass);


--
-- Name: moon moon_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon ALTER COLUMN moon_id SET DEFAULT nextval('public.moon_moon_id_seq'::regclass);


--
-- Name: planet planet_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet ALTER COLUMN planet_id SET DEFAULT nextval('public.planet_planet_id_seq'::regclass);


--
-- Name: solar_system solar_system_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.solar_system ALTER COLUMN solar_system_id SET DEFAULT nextval('public.solar_system_solar_system_id_seq'::regclass);


--
-- Name: star star_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star ALTER COLUMN star_id SET DEFAULT nextval('public.star_star_id_seq'::regclass);


--
-- Data for Name: galaxy; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.galaxy VALUES (1, 'Milky Way', 'The galaxy that includes our own solar system', true, 1.764, 265000);
INSERT INTO public.galaxy VALUES (2, 'Ursa Major III', 'The smallest known galaxy', false, 0.019, 33000);
INSERT INTO public.galaxy VALUES (3, 'Draco II', 'A dwarf sattelite galaxy orbiting around Milky Way', false, 0.003, 33000);
INSERT INTO public.galaxy VALUES (4, 'Andromeda Galaxy', 'The nearest major galaxy to  our own solar system', true, 0.152, 2500000);
INSERT INTO public.galaxy VALUES (5, 'Andromeda III', 'A dwarf galaxy orbiting around Andromeda Galaxy', false, NULL, 2650000);
INSERT INTO public.galaxy VALUES (6, 'KKR 25', 'Furthest known major galaxy', true, 0.098, 6400000);


--
-- Data for Name: moon; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.moon VALUES (1, 6, 'Kepler 68', 'Largest moon in the solar system', true, 384400);
INSERT INTO public.moon VALUES (2, 1, 'Phobos', 'Small and irregularly shaped', true, 9377);
INSERT INTO public.moon VALUES (3, 2, 'Deimos', 'Tiny moon with a smooth surface', true, 23460);
INSERT INTO public.moon VALUES (4, 3, 'Europa', 'Icy moon with a possible subsurface ocean', true, 671100);
INSERT INTO public.moon VALUES (5, 4, 'Ganymede', 'Largest moon in the solar system', true, 1070400);
INSERT INTO public.moon VALUES (6, 5, 'Callisto', 'Heavily cratered icy moon', true, 1882700);
INSERT INTO public.moon VALUES (7, 6, 'Io', 'Most volcanically active moon', true, 421700);
INSERT INTO public.moon VALUES (8, 7, 'Titan', 'Thick atmosphere with liquid methane lakes', true, 1221870);
INSERT INTO public.moon VALUES (9, 8, 'Enceladus', 'Ice-covered moon with geysers', true, 238000);
INSERT INTO public.moon VALUES (10, 10, 'Triton', 'Retrograde orbit and possible cryovolcanism', true, 354800);
INSERT INTO public.moon VALUES (11, 11, 'Oberon', 'Dark, cratered surface with ice deposits', true, 583520);
INSERT INTO public.moon VALUES (12, 14, 'Miranda', 'Strange terrain with cliffs and valleys', true, 129900);
INSERT INTO public.moon VALUES (13, 15, 'Ariel', 'Brightest moon of Uranus', true, 191020);
INSERT INTO public.moon VALUES (14, 16, 'Umbriel', 'Dark moon with mysterious bright ring', true, 266000);
INSERT INTO public.moon VALUES (15, 1, 'Charon', 'Largest moon of Pluto with a unique orbit', true, 19571);
INSERT INTO public.moon VALUES (16, 2, 'Dione', 'Moon with bright streaks on its surface', true, 377400);
INSERT INTO public.moon VALUES (17, 3, 'Rhea', 'Second-largest moon of Saturn', true, 527100);
INSERT INTO public.moon VALUES (18, 4, 'Iapetus', 'Half-bright, half-dark moon', true, 3561000);
INSERT INTO public.moon VALUES (19, 5, 'Hyperion', 'Oddly shaped and sponge-like', true, 1481000);
INSERT INTO public.moon VALUES (20, 6, 'Proteus', 'Neptune’s largest irregular moon', true, 117647);


--
-- Data for Name: planet; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.planet VALUES (1, 1, 'Mercury', 'Closest planet to the Sun, completely uninhabitable', true, 61.299);
INSERT INTO public.planet VALUES (2, 1, 'Venus', 'Hot and covered in thick clouds', true, 108.209);
INSERT INTO public.planet VALUES (3, 1, 'Earth', 'Home to diverse life forms and vast oceans', true, 149.597);
INSERT INTO public.planet VALUES (4, 1, 'Mars', 'Known as the Red Planet with a thin atmosphere', true, 227.939);
INSERT INTO public.planet VALUES (5, 1, 'Jupiter', 'The largest planet with a giant storm', true, 778.340);
INSERT INTO public.planet VALUES (6, 1, 'Saturn', 'Famous for its spectacular ring system', true, 1.426);
INSERT INTO public.planet VALUES (7, 1, 'Uranus', 'An ice giant that rotates on its side', true, 2.870);
INSERT INTO public.planet VALUES (8, 1, 'Neptune', 'Deep blue planet with extreme winds', true, 4.498);
INSERT INTO public.planet VALUES (9, 1, 'Pluto', 'Once a planet, now a dwarf planet', false, 5.906);
INSERT INTO public.planet VALUES (10, 2, 'Kepler-22b', 'An exoplanet with potential for liquid water', true, 600.500);
INSERT INTO public.planet VALUES (11, 2, 'Proxima b', 'Closest known exoplanet to Earth', true, 4.240);
INSERT INTO public.planet VALUES (12, 4, 'Gliese 581g', 'Possible habitable zone exoplanet', false, 20.500);
INSERT INTO public.planet VALUES (13, 3, 'HD 209458 b', 'Gas giant with a comet-like tail', false, 150.250);
INSERT INTO public.planet VALUES (14, 6, 'WASP-12b', 'Extremely hot planet being eaten by its star', true, 500.750);
INSERT INTO public.planet VALUES (15, 6, 'TOI-700 d', 'Exoplanet in the habitable zone', true, 100.999);
INSERT INTO public.planet VALUES (16, 6, '55 Cancri e', 'Lava-covered super-Earth', true, 40.450);


--
-- Data for Name: solar_system; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.solar_system VALUES (1, 'Sun-Earth', 1, 3);
INSERT INTO public.solar_system VALUES (2, 'Lalande 21185-TOI 700', 3, 15);
INSERT INTO public.solar_system VALUES (3, 'Mu Arae-Earth', 6, 16);


--
-- Data for Name: star; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.star VALUES (1, 1, 'The Sun', 'This is the star which our own solar system is made out of', true, 4600.000);
INSERT INTO public.star VALUES (2, 1, 'Proxima Century', 'Nearest star to earth with a planetary system', true, 4850.000);
INSERT INTO public.star VALUES (3, 4, 'Lalande 21185', 'A star in the south of Andromeda', true, 8047.000);
INSERT INTO public.star VALUES (4, 1, 'Rigil Kentaurus', 'A Star in Milky Way', false, 320.000);
INSERT INTO public.star VALUES (5, 6, '82 Eridani', 'Not much known', false, NULL);
INSERT INTO public.star VALUES (6, 6, 'Mu Arae', 'This is a star similar to the Sun', true, 5200.000);


--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.galaxy_galaxy_id_seq', 6, true);


--
-- Name: moon_moon_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.moon_moon_id_seq', 20, true);


--
-- Name: planet_planet_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.planet_planet_id_seq', 16, true);


--
-- Name: solar_system_solar_system_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.solar_system_solar_system_id_seq', 3, true);


--
-- Name: star_star_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.star_star_id_seq', 6, true);


--
-- Name: galaxy galaxy_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_name_key UNIQUE (name);


--
-- Name: galaxy galaxy_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_pkey PRIMARY KEY (galaxy_id);


--
-- Name: moon moon_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_name_key UNIQUE (name);


--
-- Name: moon moon_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_pkey PRIMARY KEY (moon_id);


--
-- Name: planet planet_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_name_key UNIQUE (name);


--
-- Name: planet planet_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_pkey PRIMARY KEY (planet_id);


--
-- Name: solar_system solar_system_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.solar_system
    ADD CONSTRAINT solar_system_name_key UNIQUE (name);


--
-- Name: solar_system solar_system_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.solar_system
    ADD CONSTRAINT solar_system_pkey PRIMARY KEY (solar_system_id);


--
-- Name: star star_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_name_key UNIQUE (name);


--
-- Name: star star_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_pkey PRIMARY KEY (star_id);


--
-- Name: moon moon_planet_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_planet_id_fkey FOREIGN KEY (planet_id) REFERENCES public.planet(planet_id);


--
-- Name: planet planet_star_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_star_id_fkey FOREIGN KEY (star_id) REFERENCES public.star(star_id);


--
-- Name: solar_system solar_system_planet_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.solar_system
    ADD CONSTRAINT solar_system_planet_id_fkey FOREIGN KEY (planet_id) REFERENCES public.planet(planet_id);


--
-- Name: solar_system solar_system_star_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.solar_system
    ADD CONSTRAINT solar_system_star_id_fkey FOREIGN KEY (star_id) REFERENCES public.star(star_id);


--
-- Name: star star_galaxy_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_galaxy_id_fkey FOREIGN KEY (galaxy_id) REFERENCES public.galaxy(galaxy_id);


--
-- PostgreSQL database dump complete
--

