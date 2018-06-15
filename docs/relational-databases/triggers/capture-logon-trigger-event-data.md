---
title: Capturar datos de eventos de desencadenador logon | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: triggers
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
caps.latest.revision: 5
author: rothja
ms.author: jroth
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3dd14622a5c427998b37a270bc29d635b324d967
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "33005982"
---
# <a name="capture-logon-trigger-event-data"></a>Capturar datos de eventos de desencadenador logon
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]
  Para capturar datos XML acerca de los eventos LOGON para utilizarlos dentro de los desencadenadores logon, utilice la función [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md) . El evento LOGON devuelve el siguiente esquema de datos de eventos:  
  
 `<EVENT_INSTANCE>`  
  
 `<EventType>event_type</EventType>`  
  
 `<PostTime>post_time</PostTime>`  
  
 `<SPID>spid</SPID>`  
  
 `<ServerName>server_name</ServerName>`  
  
 `<LoginName>login_name</LoginName>`  
  
 `<LoginType>login_type</LoginType>`  
  
 `<SID>sid</SID>`  
  
 `<ClientHost>client_host</ClientHost>`  
  
 `<IsPooled>is_pooled</IsPooled>`  
  
 `</EVENT_INSTANCE>`  
  
 `<EventType>`  
 Contiene `LOGON`.  
  
 `<PostTime>`  
 Contiene la hora en la que se solicita que se establezca una sesión.  
  
 `<SID>`  
 Contiene el flujo binario codificado de base 64 del número de identificación de seguridad (SID) para el nombre de inicio de sesión especificado.  
  
 `<ClientHost>`  
 Contiene el nombre de host del cliente desde el que se realiza la conexión. El valor es '`<local_machine>`' si el nombre del cliente y del servidor son iguales. De lo contrario, el valor es la dirección IP del cliente.  
  
 `<IsPooled>`  
 Es `1` si la conexión se vuelve a utilizar empleando la agrupación de conexiones. De lo contrario, el valor es `0`.  
  
  
