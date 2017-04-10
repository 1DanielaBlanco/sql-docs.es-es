---
title: "Cmdlet New-RestoreFolder | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5938b3a9-6412-45fc-86f8-264651d01598
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Cmdlet New-RestoreFolder
  Restaura una carpeta original en una nueva carpeta.  
  
## Sintaxis  
 `New-RestoreFolder [-OriginalFolder] <String> [-NewFolder] <String> [-AsTemplate] [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 `New-RestoreFolder [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 Los parámetros comunes, como –Verbose, -Debug, parámetros de error y advertencia, -Whatif y –Confirm, se incluyen en la referencia de Windows PowerShell. Para obtener más información, vea [about_Commonparameters](http://technet.microsoft.com/library/dd315352.aspx).  
  
## Description  
 El cmdlet New-RestoreFolder se utiliza para crear una nueva carpeta basándose en el nombre de la carpeta original.  
  
## Parámetros  
  
### -OriginalFolder \<cadena>  
 Obtiene la ubicación original de la carpeta.  
  
|||  
|-|-|  
|¿Requerido?|true|  
|¿Posición?|0|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|true|  
|¿Aceptar caracteres comodín?|false|  
  
### -NewFolder \<cadena>  
 Establece la ubicación de una nueva carpeta.  
  
|||  
|-|-|  
|¿Requerido?|true|  
|¿Posición?|1|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|true|  
|¿Aceptar caracteres comodín?|false|  
  
### -AsTemplate \<SwitchParameter>  
 Especifica si el objeto se debe crear en la memoria y devolver.  
  
|||  
|-|-|  
|¿Requerido?|false|  
|¿Posición?|con nombre|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|false|  
|¿Aceptar caracteres comodín?|false|  
  
### -Server \<cadena>  
 Especifica la instancia de Analysis Services a la que el cmdlet se conectará y ejecutará. Si no se proporciona un nombre de servidor, se establecerá una conexión al host local. Para las instancias predeterminadas, especifique solo el nombre del servidor. Para las instancias con nombre, utilice el formato nombreDeServidor\nombreDeInstancia. En las conexiones HTTP, utilice el formato http[s]://server[:port]/virtualdirectory/msmdpump.dll.  
  
|||  
|-|-|  
|¿Requerido?|false|  
|¿Posición?|con nombre|  
|Valor predeterminado|localhost|  
|¿Aceptar la entrada de la canalización?|false|  
|¿Aceptar caracteres comodín?|false|  
  
### -Credential \<PSCredential>  
 Este parámetro se utiliza para pasar un nombre de usuario y una contraseña cuando se utiliza una conexión HTTP a una instancia de Analysis Services, para una instancia que ha configurado para el acceso HTTP. Para obtener más información, vea [Configurar el acceso HTTP a Analysis Services en Internet Information Services &#40;IIS&#41; 8.0](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md) y [Scripting de PowerShell en Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md) para conexiones HTTP.  
  
 Si se especifica este parámetro, el nombre de usuario y la contraseña se utilizarán para conectarse a la instancia de Analysis Server especificada. Si no se especifica ninguna credencial, se utilizará la cuenta predeterminada de Windows del usuario que ejecuta la herramienta.  
  
 Para usar este parámetro, cree primero un objeto PSCredential con Get-Credential para especificar el nombre de usuario y la contraseña (por ejemplo, `$Cred=Get-Credential “adventure-works\bobh”`. Después, puede canalizar este objeto al parámetro –Credential `(-Credential:$Cred`).  
  
|||  
|-|-|  
|¿Requerido?|false|  
|¿Posición?|con nombre|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|True (ByValue)|  
|¿Aceptar caracteres comodín?|false|  
  
## Entradas y salidas  
 El tipo de entrada es el tipo de objetos que se pueden canalizar al cmdlet. El tipo de valor devuelto es el tipo de objeto que el cmdlet devuelve.  
  
|||  
|-|-|  
|Entradas||  
|Salidas|None|  
  
## Ejemplos  
  
## Vea también  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Administrar modelos tabulares con PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  