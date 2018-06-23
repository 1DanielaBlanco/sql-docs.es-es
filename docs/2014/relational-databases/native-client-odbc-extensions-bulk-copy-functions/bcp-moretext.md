---
title: bcp_moretext | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_moretext
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_moretext function
ms.assetid: 23e98015-a8e4-4434-9b3f-9c7350cf965f
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 22b9c6345b3dcdbb2a1b6bc5db735dcb2d635f5d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36196909"
---
# <a name="bcpmoretext"></a>bcp_moretext
  Envía parte de un valor de tipo de datos largo, de longitud variable a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
RETCODE bcp_moretext (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
LPCBYTE   
pData  
);  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *HDBC*  
 Es el identificador de la conexión ODBC habilitada para la copia masiva.  
  
 *cbData*  
 Es el número de bytes de datos se copian a SQL Server de los datos al que hace referencia *pData*. Un valor de SQL_NULL_DATA indica NULL.  
  
 *pData*  
 Es un puntero al fragmento de datos compatible, largo y de longitud variable que se va a enviar a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="returns"></a>Devuelve  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Notas  
 Esta función puede utilizarse junto con [bcp_bind](bcp-bind.md) y [bcp_sendrow](bcp-sendrow.md) long, copiar valores de datos de longitud variable a SQL Server en un número de fragmentos más pequeños. **bcp_moretext** puede utilizarse con columnas que tienen los siguientes tipos de datos de SQL Server: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, tipo definido por el usuario (UDT) y XML. **bcp_moretext** admite conversiones de datos, los datos proporcionados deben coincidir con el tipo de datos de la columna de destino.  
  
 Si **bcp_bind** se llama con un NULL *pData* parámetro para los tipos de datos que son compatibles con **bcp_moretext**, `bcp_sendrow` envía el valor de datos completa, sin tener en cuenta de longitud. Si es, sin embargo, **bcp_bind** tiene un valor nulo *pData* parámetro para los tipos de datos admitidos, **bcp_moretext** puede utilizarse para copiar datos inmediatamente después de una devolución correcta de `bcp_sendrow` que indica que se han procesado las columnas enlazadas con los datos presentes.  
  
 Si usa **bcp_moretext** para enviar una columna de tipo de datos admitidos en una fila, también debe utilizarlo para enviar todas las demás columnas de tipo de datos admitidos en la fila. No se puede omitir ninguna columna. Los tipos de datos admitidos son SQLTEXT, SQLNTEXT, SQLIMAGE, SQLUDT y SQLXML. SQLCHARACTER, SQLVARCHAR, SQNCHAR, SQLBINARY y SQLVARBINARY también pertenecen a esta categoría si la columna es de tipo varchar (max), nvarchar (max) o varbinary (max), respectivamente.  
  
 Una llamada a **bcp_bind** o [bcp_collen](bcp-collen.md) establece la longitud total de todos los elementos de datos que se copiará en la columna de SQL Server. Un intento de envío de SQL Server más bytes que los especificados en la llamada a **bcp_bind** o `bcp_collen` genera un error. Este error se producirá, por ejemplo, en una aplicación que utiliza `bcp_collen` para establecer la longitud de datos disponibles para un servidor SQL Server `text` columna a 4500, a continuación, se denomina **bcp_moretext** cinco veces al que se indica en cada llamada que los datos de longitud del búfer era de 1000 bytes.  
  
 Si una fila copiada contiene más de una columna larga, de longitud variable, **bcp_moretext** envía primero sus datos con el menor número ordinal de columna, seguida por el siguiente más bajo número ordinal de columna y así sucesivamente. Es importante una configuración correcta de la longitud total de datos esperados. No hay ninguna manera de indicar, fuera de la configuración de longitud, que la copia masiva ha recibido todos los datos de una columna.  
  
 Cuando `var(max)` valores se envían al servidor con bcp_sendrow y bcp_moretext, no es necesario llamar a bcp_collen para establecer la longitud de columna. En su lugar, únicamente para estos tipos, el valor termina con bcp_sendrow que realiza la llamada con una longitud de cero.  
  
 Una aplicación suele llamar `bcp_sendrow` y **bcp_moretext** dentro de los bucles para enviar un número de filas de datos. Este es un resumen de cómo hacer esto en una tabla que contiene dos `text` columnas:  
  
```  
while (there are still rows to send)  
{  
bcp_sendrow(...);  
  
for (all the data in the first varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
for (all the data in the second varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
}  
  
```  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo muestra cómo usar **bcp_moretext** con **bcp_bind** y `bcp_sendrow`:  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      idRow = 5;  
char*      pPart1 = "This text value isn't very long,";  
char*      pPart2 = " but it's broken into three parts";  
char*      pPart3 = " anyhow.";  
DBINT      cbAllParts;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, "comdb..articles", NULL, NULL, DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idRow, 0, SQL_VARLEN_DATA, NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
cbAllParts = (DBINT) (strnlen(pPart1, sizeof(pPart1) + 1) + strnlen(pPart2, sizeof(pPart2) + 1) + strnlen(pPart3, sizeof(pPart3) + 1));  
if (bcp_bind(hdbc, NULL, 0, cbAllParts, NULL, 0, SQLTEXT, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Send this row, with the text value broken into three chunks.   
if (bcp_sendrow(hdbc) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart1, sizeof(pPart1) + 1), pPart1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart2, sizeof(pPart2) + 1), pPart2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart3, sizeof(pPart3) + 1), pPart3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// All done. Get the number of rows processed (should be one).  
nRowsProcessed = bcp_done(hdbc);  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Vea también  
 [Funciones de copia masiva](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  