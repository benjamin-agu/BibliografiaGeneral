-- Adminer 5.4.1 MySQL 8.0.44 dump

SET NAMES utf8;
SET time_zone = '+00:00';
SET foreign_key_checks = 0;
SET sql_mode = 'NO_AUTO_VALUE_ON_ZERO';

SET NAMES utf8mb4;

CREATE DATABASE `USUARIOS` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci */ /*!80016 DEFAULT ENCRYPTION='N' */;
USE `USUARIOS`;

CREATE TABLE `resaltados` (
  `id_resaltado` int NOT NULL AUTO_INCREMENT,
  `id_usuario` int NOT NULL,
  `id_texto` int NOT NULL,
  `fuente` enum('biblioteca','enciclopedia') NOT NULL DEFAULT 'biblioteca' COMMENT 'Origen del contenido resaltado',
  `texto_seleccionado` text NOT NULL,
  `contexto_previo` text,
  `contexto_posterior` text,
  `offset_inicio` int DEFAULT NULL,
  `offset_final` int DEFAULT NULL,
  `color` varchar(7) DEFAULT '#ffeb3b',
  `tipo` enum('resaltado','subrayado','comentario') NOT NULL DEFAULT 'resaltado' COMMENT 'Modo de anotación sobre el texto',
  `estilo_subrayado` enum('solido','punteado','ondulado','ninguno') NOT NULL DEFAULT 'ninguno' COMMENT 'Estilo de línea — ninguno = solo color de fondo',
  `color_tinta` enum('negro','rojo') NOT NULL DEFAULT 'negro' COMMENT 'Color de la línea de subrayado: negro estándar o rojo (maestro)',
  `comentario` text,
  `fecha_creacion` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  `fecha_modificacion` timestamp NULL DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP COMMENT 'Última edición — NULL si nunca se ha editado',
  `tematicas_ids` json DEFAULT NULL COMMENT 'Array JSON con los id_tematica asociados a este resaltado',
  PRIMARY KEY (`id_resaltado`),
  KEY `id_usuario` (`id_usuario`),
  KEY `id_texto` (`id_texto`),
  KEY `idx_texto_fuente` (`id_texto`,`fuente`,`id_usuario`),
  KEY `idx_tipo` (`tipo`),
  FULLTEXT KEY `ft_resaltado_texto` (`texto_seleccionado`,`comentario`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

INSERT INTO `resaltados` (`id_resaltado`, `id_usuario`, `id_texto`, `fuente`, `texto_seleccionado`, `contexto_previo`, `contexto_posterior`, `offset_inicio`, `offset_final`, `color`, `tipo`, `estilo_subrayado`, `color_tinta`, `comentario`, `fecha_creacion`, `fecha_modificacion`, `tematicas_ids`) VALUES



(12,	1,	16,	'biblioteca',	'Brother, that was some storm.',	'h and I took it down along; and when it was daylight I was off Eastern Harbor.\n\n',	' I was the first boat out and you never saw water like that was. It was just as ',	1496,	1525,	'#ffcc80',	'resaltado',	'ninguno',	'negro',	'¡Vaya tormenta!',	'2026-02-27 06:16:50',	'2026-03-22 05:19:58',	'[233, 120]'),
(13,	1,	20,	'biblioteca',	'Me crucifican y yo debo ser la cruz y los clavos.',	'El cómplice\n\n\n\n',	'\nMe tienden la copa y yo debo ser la cicuta.\nMe engañan y yo debo ser la mentira',	15,	64,	'#ffeb3b',	'resaltado',	'ninguno',	'negro',	'',	'2026-02-27 20:34:42',	'2026-03-22 05:19:58',	'[110, 141, 160]'),
(19,	1,	14,	'biblioteca',	'Will I wait a lonely lifetime?',	'Who knows how long I\'ve loved you,\nYou know I love you still.\n',	'\nIf you want me to I will.\nFor if I ever saw you\nI didn\'t catch your name.\nBut i',	62,	92,	'#90caf9',	'resaltado',	'ninguno',	'negro',	'¿Es esta una promesa de abnegación imprudente o de lealtad encomiable? Depende de la época...',	'2026-02-28 01:41:05',	'2026-03-22 05:19:58',	'[110]'),
(20,	1,	1,	'enciclopedia',	'La polifonía es un tipo de textura musical...',	'',	'',	0,	45,	'#90caf9',	'resaltado',	'ninguno',	'negro',	'',	'2026-02-28 07:07:50',	'2026-03-22 05:19:58',	'[52]'),
(21,	1,	11,	'biblioteca',	'Als Gregor Samsa eines Morgens aus unruhigen Träumen erwachte, fand er sich in seinem Bett zu einem ungeheueren Ungeziefer verwandelt.',	'DIE VERWANDLUNG\n\n\n\n\nI.\n\n\n\n',	' Er lag auf seinem panzerartig harten Rücken und sah, wenn er den Kopf ein wenig',	26,	160,	'#ffeb3b',	'resaltado',	'ninguno',	'negro',	'Una línea de apertura memorable.',	'2026-02-28 16:12:03',	'2026-03-22 05:19:58',	'[236, 127]'),
(25,	1,	9,	'biblioteca',	'Aujourd\'hui, maman est morte.',	'L’ÉTRANGER\nPremière partie\nI\n\n',	' Ou peut-être hier, je ne sais pas. J\'ai reçu un télégramme de l\'asile : « Mère ',	30,	59,	'#ffeb3b',	'resaltado',	'ninguno',	'negro',	'Esta es una gran introducción.',	'2026-03-01 19:05:20',	'2026-03-22 05:19:58',	'[26]'),
(30,	1,	26,	'biblioteca',	'That government is best which governs least',	'ON THE DUTY OF CIVIL DISOBEDIENCE\n\nI heartily accept the motto,—“',	';” and I should like to see it acted up to more rapidly and systematically. Carr',	65,	108,	'#f48fb1',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-04 20:20:23',	'2026-03-22 05:19:58',	'[]'),
(31,	1,	31,	'biblioteca',	'I ask not good-fortune, I myself am good-fortune',	' before me,\nThe long brown path before me leading wherever I choose.\nHenceforth ',	',\nHenceforth I whimper no more, postpone no more, need nothing,\nDone with indoor',	178,	226,	'#ffeb3b',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-04 20:21:15',	'2026-03-22 05:19:58',	'[]'),
(36,	1,	31,	'biblioteca',	'I carry them, men and women, I carry them with me wherever I go,I swear it is impossible for me to get rid of them',	'',	'',	-1,	113,	'#a5d6a7',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-04 20:37:14',	'2026-03-22 05:19:58',	'[]'),
(37,	1,	27,	'biblioteca',	'And her aunts were not quite sure how they felt about it,But they knew that it was modern.',	'',	'',	-1,	89,	'#ffeb3b',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-04 20:39:05',	'2026-03-22 05:19:58',	'[]'),
(38,	1,	39,	'biblioteca',	'la muerte, ese otro mar',	'da es corta\ny aunque las horas son tan largas, una\noscura maravilla nos acecha,\n',	', esa otra flecha\nque nos libra del sol y de la luna\ny del amor. La dicha que me',	730,	753,	'#ffcc80',	'resaltado',	'ninguno',	'negro',	'¿Acaso la muerte es una empresa en el pensamiento Borgiano?',	'2026-03-04 23:13:31',	'2026-03-22 05:19:58',	'[7, 69, 120]'),
(40,	1,	37,	'biblioteca',	'How dreary — to be — Somebody!',	'obody — too?\nThen there\'s a pair of us!\nDont tell! they\'d banish us - you know! ',	'\nHow public — like a Frog —\nTo tell your name — the livelong June —\nTo an admiri',	142,	172,	'#ffeb3b',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-05 00:22:19',	'2026-03-22 05:19:58',	'[127, 3]'),
(41,	1,	40,	'biblioteca',	'In this short Life that only lasts an hour\nHow much —how little— is within our power',	'In this short Life\n\n',	'',	20,	104,	'#ffcc80',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-05 00:37:01',	'2026-03-22 05:19:58',	'[12, 18]'),
(43,	1,	35,	'biblioteca',	'Here are our thoughts—voyagers’ thoughts',	'haply will I, a reminiscence of the land, be read,\nIn full rapport at last.\n\n2\n\n',	',\nHere not the land, firm land, alone appears, may then by them be said;\nThe sky',	469,	509,	'#ffeb3b',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-05 22:32:34',	'2026-03-22 05:19:58',	'[232, 37, 275]'),
(44,	1,	52,	'biblioteca',	'even I myself I often think know little or nothing of my real life',	'm dead and gone write my life?\n(As if any man really knew aught of my life,\nWhy ',	',\nOnly a few hints, a few diffused faint clews and indirections\nI seek for my ow',	237,	303,	'#f48fb1',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-06 00:21:03',	'2026-03-22 05:19:58',	'[12, 259, 275]'),
(46,	1,	39,	'biblioteca',	'Ya no es mágico el mundo',	'1964\nI\n\n',	'. Te han dejado.\nYa no compartirás la clara luna\nni los lentos jardines. Ya no h',	8,	32,	'#90caf9',	'resaltado',	'ninguno',	'negro',	'Este elogio a la juventud es un vituperio a la vejez, me parece.',	'2026-03-19 04:58:10',	'2026-03-22 05:19:58',	'[18]'),
(48,	1,	10,	'biblioteca',	'He was an old man who fished alone in a skiff in the Gulf Stream and he had gone eighty-four days now without taking a fish.',	'THE OLD MAN AND THE SEA\n\n',	' In the first forty days a boy had been with him. But after forty days without a',	25,	149,	'#ffeb3b',	'resaltado',	'ninguno',	'negro',	'En una primera línea se mencionan dos cosas de suma importancia: la vejez y la soledad (además de una contextualización exitosa: el pescador que no ha pescado en muchos días).',	'2026-03-19 05:16:11',	'2026-03-22 05:19:58',	'[]'),
(49,	1,	19,	'biblioteca',	'yararacusú',	' la mordedura en el pie. Saltó adelante, y al volverse con un juramento vio una ',	' que arrollada sobre sí misma, esperaba otro ataque.\n\nEl hombre echó una veloz o',	142,	152,	'#a5d6a7',	'resaltado',	'ninguno',	'negro',	'Especie de serpiente.',	'2026-03-22 03:26:24',	'2026-03-22 05:19:58',	'[117]'),
(50,	1,	10,	'biblioteca',	'Now is no time to think of what you do not have. Think of what you can do with what there is.',	'ould have brought many things, he thought. But you did not bring them, old man. ',	'\n\n“You give me much good counsel,” he said aloud. “I’m tired of it.”\n\nHe held th',	115478,	115571,	'#ffcc80',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-22 04:26:54',	'2026-03-22 05:19:58',	'[39]'),
(56,	1,	31,	'biblioteca',	'I do not want the constellations any nearer,\nI know they are very well where they are',	'isms,\nStrong and content I travel the open road.\nThe earth, that is sufficient,\n',	',\nI know they suffice for those who belong to them.\n(Still here I carry my old d',	426,	511,	'#ffcc80',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-22 05:29:49',	NULL,	'[]'),
(57,	1,	12,	'biblioteca',	'I love you like the little bird\nThat picks up crumbs around the door',	'',	'',	-1,	67,	'#a5d6a7',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-22 05:31:30',	NULL,	'[]'),
(62,	1,	39,	'biblioteca',	'sol de agonías',	' jardines. Ya no hay una\nluna que no sea espejo del pasado,\ncristal de soledad, ',	'.\nAdiós las mutuas manos y las sienes\nque acercaba el amor. Hoy sólo tienes\nla f',	174,	188,	'#c0392b',	'comentario',	'ninguno',	'negro',	'ironía',	'2026-03-22 22:06:04',	'2026-03-22 22:15:15',	'[10]'),
(65,	1,	39,	'biblioteca',	'un instante cualquiera es más profundo\ny diverso que el mar',	'\n\nII\n\nYa no seré feliz. Tal vez no importa.\nHay tantas otras cosas en el mundo;\n',	'. La vida es corta\ny aunque las horas son tan largas, una\noscura maravilla nos a',	584,	643,	'#b0bec5',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-22 22:17:03',	NULL,	'[69]'),
(66,	1,	19,	'biblioteca',	'una somnolencia llena de recuerdos',	'ue antes de tres horas estaría en Tacurú-Pucú.\n\nEl bienestar avanzaba, y con él ',	'. No sentía ya nada ni en la pierna ni en el vientre. ¿Viviría aún su compadre G',	4881,	4915,	'#ffcc80',	'resaltado',	'ninguno',	'negro',	'Preámbulo de la muerte.',	'2026-03-22 22:42:40',	'2026-03-22 22:43:10',	'[155, 259]'),
(67,	1,	39,	'biblioteca',	'arte del olvido',	' que no tiene y no ha tenido\nnunca, pero no basta ser valiente\npara aprender el ',	'.\nUn símbolo, una rosa, te desgarra\ny te puede matar una guitarra.\n\n\nII\n\nYa no s',	422,	437,	'#ffeb3b',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-22 22:44:29',	NULL,	'[227]'),
(68,	1,	39,	'biblioteca',	'Nadie pierde (repites vanamente)\nsino lo que no tiene y no ha tenido\nnunca',	'nes\nque acercaba el amor. Hoy sólo tienes\nla fiel memoria y los desiertos días.\n',	', pero no basta ser valiente\npara aprender el arte del olvido.\nUn símbolo, una r',	302,	376,	'#f48fb1',	'resaltado',	'ninguno',	'negro',	'',	'2026-03-22 22:53:59',	NULL,	'[231]'),
(70,	1,	39,	'biblioteca',	'el goce de estar triste',	'aprender el arte del olvido.\nUn símbolo, una rosa, te desgarra\ny te puede matar una guitarra.\n\n\nII\n\nYa no seré feliz. Tal vez no importa.\nHay tantas otras cosas en el mundo;\nun instante cualquiera es más profundo\ny diverso que el mar. La vida es corta\ny aunque las horas son tan largas, una\noscura maravilla nos acecha,\nla muerte, ese otro mar, esa otra flecha\nque nos libra del sol y de la luna\ny del amor. La dicha que me diste\ny me quitaste debe ser borrada;\nlo que era todo tiene que ser nada.\nSólo me queda ',	',\nesa vana costumbre que me inclina\nal Sur, a cierta puerta, a cierta esquina.',	922,	945,	'#ffeb3b',	'resaltado',	'solido',	'rojo',	'',	'2026-03-24 02:16:10',	NULL,	'[]'),
(103,	1,	39,	'biblioteca',	'ni los lentos jardines',	NULL,	NULL,	NULL,	NULL,	'#ffeb3b',	'resaltado',	'ninguno',	'negro',	NULL,	'2026-03-25 00:17:48',	NULL,	NULL);

-- 2026-06-21 20:36:46 UTC

