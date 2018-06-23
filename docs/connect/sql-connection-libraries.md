---
title: Bibliotecas de conexiones de bases de datos de SQL de Microsoft | Documentos de Microsoft
description: Proporciona vínculos de descarga para los módulos que permiten la conexión a Microsoft SQL Server y base de datos de SQL Azure, desde una variedad de lenguajes de programación de cliente.
author: MightyPen
ms.suite: sql
ms.prod: sql
ms.prod_service: connectivity
ms.technology: dbe-data-tier-apps
ms.custom: ''
ms.topic: article
ms.date: 06/18/2018
ms.author: genemi
ms.openlocfilehash: b7d00ed25392e979cc0d5037bef6b7d8eccc66bf
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36246847"
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Módulos de conexión para bases de datos SQL de Microsoft

Este artículo contiene vínculos de descarga a los módulos de conexión o *controladores* que los programas cliente pueden utilizar para interactuar con [Microsoft SQL Server](../relational-databases/database-features.md)y con su gemelas en la nube [Azure Base de datos SQL](http://docs.microsoft.com/azure/sql-database/). Controladores estén disponibles para una amplia variedad de lenguajes de programación, con los siguientes sistemas operativos:

- Linux (Ubuntu)
- macOS
- Windows

#### <a name="oop-to-relational-mismatch"></a>Error de coincidencia de programación orientada a objetos a relacional

*Relacional*: los programas de cliente que se escriben en un lenguaje de (OOP) de programación orientada a objetos a menudo utilizan controladores para SQL Server que devuelven datos consultados en un formato que es más relacional que orientado a objetos. Uso de ADO.NET en C# es un ejemplo. La programación orientada a objetos relacionales discrepancia de formato a veces hace que el código de programación orientada a objetos sea más difícil de escribir y entender.

*ORM*: otros controladores o marcos de devuelvan los datos consultados en el formato de la programación orientada a objetos, evitar la falta de coincidencia. Estos controladores de trabajo se espera que las clases se han definido para que coincida con las columnas de datos de tablas SQL. El controlador, a continuación, realiza la *asignación objeto-relacional* (ORM) para devolver los datos consultados como una instancia de una clase. Entity Framework (EF de Microsoft) en C# e hibernación para Java, son dos ejemplos.

El presente artículo dedica secciones independientes para estos dos tipos de controladores de conexión.

<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>Controladores para acceso relacional


<!--
Each given Microsoft Download Center page should be enhanced
with a link to the next NEWER version page, on the day that the
original page is no longer the latest because the newer page is being added.
But this policy is not agreed on or observed,
putting the links in the following table at risk for being outdated.

PHP driver in Github.com also uses this FWLink:  http://go.microsoft.com/fwlink/?LinkID=518036 ,
although the FWLink is less precise than is http://github.com/Microsoft/msphpsql/tree/dev#install-unix .
-->

| Idioma | Descargue el controlador SQL |
| :------- | :---------------------- |
| C# | [ADO.NET](http://www.microsoft.com/net/download/)<br /><br />[Núcleo de. NET, para Ubuntu Linux](https://www.microsoft.com/net/core#Ubuntu)<br />[Núcleo de. NET, para MacOS](https://www.microsoft.com/net/core#macos)<br />[Núcleo de. NET, para Windows](https://www.microsoft.com/net/core) |
| C++ | [ODBC](./odbc/download-odbc-driver-for-sql-server.md)<br /><br />[OLE DB](./oledb/download-oledb-driver-for-sql-server.md) |
| Java | [JDBC](./jdbc/download-microsoft-jdbc-driver-for-sql-server.md) |
| Node.js | [Controlador de Node.js, las instrucciones de instalación](./node-js/step-1-configure-development-environment-for-node-js-development.md) |
| PHP | [PHP](./php/download-drivers-php-sql-server.md) |
| Python | [pyodbc, las instrucciones de instalación](./python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development.md)<br />[Descargar ODBC](./odbc/download-odbc-driver-for-sql-server.md) |
| Ruby | [Controlador Ruby, las instrucciones de instalación](./ruby/step-1-configure-development-environment-for-ruby-development.md)<br />[Página de descarga Ruby](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |

<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Controladores para el acceso ORM


En la tabla siguiente se muestra ejemplos de marcos de trabajo de asignación relacional de objetos (ORM) que las aplicaciones cliente utilizan para conectarse a bases de datos SQL de Microsoft.


| Idioma | Descarga del controlador ORM |
| :------- | :------------------ |
| C# | [Entity Framework Core](http://docs.microsoft.com/ef/core/)<br />[Entity Framework (6.x o posterior)](http://docs.microsoft.com/ef/) |
| Java | [Hibernación ORM](http://hibernate.org/orm)|
| PHP | [ORM elocuente, que se incluye en la instalación de Laravel](http://laravel.com/docs/) |
| Node.js | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | [Django](http://www.djangoproject.com/) |
| Ruby | [Ruby sobre raíles](http://rubyonrails.org/) |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Generar una aplicación las páginas Web
[http://aka.ms/sqldev](http://aka.ms/sqldev) le lleva a un conjunto de *compilación una aplicación* las páginas Web. Las páginas Web proporcionan información acerca de diversas combinaciones de idioma, el sistema operativo y el controlador de conexión de SQL de la programación. Entre la información proporcionada por las páginas de generar una aplicación Web se encuentran los siguientes elementos:

- Obtener más información acerca de cómo empezar a trabajar desde el principio, para cada combinación de idioma, sistema operativo + controlador.
    - Instrucciones para instalar a los controladores más recientes de conexión de SQL.
- Ejemplos de código para cada uno de los siguientes elementos:
    - Ejemplos de código objeto relacional.
    - Ejemplos de código ORM.
    - Demostraciones de índice de almacén de columnas para un rendimiento mucho más rápido.

#### <a name="first-page-of-build-an-app-webpages"></a>Primera página, de las páginas de generar una aplicación Web
![Generar una aplicación las páginas Web, primera captura de pantalla de página][image-ref-163-buildanapp-webpages-first-page]

#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Menú de Java - Ubuntu, de las páginas de generar una aplicación Web
![Generar una aplicación las páginas Web, menú Ubuntu de Java][image-ref-167-buildanapp-webpages-menu-java-ubuntu]

&nbsp;

## <a name="related-links"></a>Vínculos relacionados
- [Ejemplos de código para conectarse a la base de datos de SQL de Azure en la nube, con Java y otros lenguajes](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java).

<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
