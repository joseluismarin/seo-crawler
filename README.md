# seo-crawler
Seo Crawler es un sencillo programa en Python cuya función es la de obtener información relevante para el SEO de las webs que va encontrando.


Seo Crawler necesita de una base de datos en MySQL para almacenar y obtener información.
En un primer momento con estas dos tablas será suficiente:


CREATE TABLE `dominios` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`dominio` VARCHAR(50) NULL DEFAULT NULL,
	`protocolo` VARCHAR(50) NULL DEFAULT 'http',
	`subdominio` VARCHAR(50) NULL DEFAULT '',
	`estado` INT(11) NULL DEFAULT '-1',
	PRIMARY KEY (`id`),
	UNIQUE INDEX `dominio` (`dominio`)
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB;

CREATE TABLE `scrap` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`dominio` VARCHAR(500) NULL DEFAULT NULL,
	`url` VARCHAR(500) NULL DEFAULT NULL,
	`etiqueta` VARCHAR(500) NULL DEFAULT NULL,
	`atributo` VARCHAR(500) NULL DEFAULT NULL,
	`valor` VARCHAR(500) NULL DEFAULT NULL,
	`texto` VARCHAR(500) NULL DEFAULT NULL,
	`control` VARCHAR(500) NULL DEFAULT NULL,
	PRIMARY KEY (`id`),
	UNIQUE INDEX `control` (`control`)
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB
;

También será necesario introducir un primer registro del que partirá nuestro primer scrapeo:
INSERT INTO `SCRAPERS_YT`.`dominios` (`id`, `dominio`, `protocolo`) VALUES ('1', 'elpais.es', 'https');

Una vez teniendo preparada la BD, simplemente hay que modificar las variables de conexión a la base de datos dentro de "seo-crawler.py":
host="HOST",
user="USER",
passwd="PASS", 
database="DATABASE"

¡Finalmente ejecutar "seo-crawler.py" y ver los resultados!

