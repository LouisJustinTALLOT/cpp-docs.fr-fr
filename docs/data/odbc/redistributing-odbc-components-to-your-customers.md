---
title: Redistribution des composants ODBC à vos clients | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e0427228b8fb3e852cf1d9ee66a10c9290b860b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090222"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redistribution des composants ODBC à vos clients
Si vous incorporez la fonctionnalité des programmes administrateur ODBC dans votre application, vous devez également distribuer à vos utilisateurs les fichiers qui exécutent ces programmes. Ces fichiers ODBC se trouvent dans le répertoire \OS\System du CD-ROM Visual C++. Le fichier Redistrb.wri et le contrat de licence dans le même répertoire contiennent une liste des fichiers ODBC que vous pouvez redistribuer.  
  
 Consultez la documentation pour les pilotes ODBC que vous prévoyez d’expédier. Vous devez déterminer quelles DLL et autres fichiers à expédier. Vous devez également lire [redistribution des composants ODBC à vos clients](../../data/odbc/redistributing-odbc-components-to-your-customers.md), qui explique comment redistribuer des composants ODBC.  
  
 En outre, vous devez inclure un autre fichier dans la plupart des cas. Le Odbccr32.dll est la bibliothèque de curseurs ODBC. Cette bibliothèque permet de pilotes de niveau 1 de défilement vers l’avant et vers l’arrière. Il fournit également la possibilité de prendre en charge des instantanés. Pour plus d’informations sur la bibliothèque de curseurs ODBC, consultez [ODBC : bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
 Les rubriques suivantes fournissent plus d’informations sur l’utilisation de ODBC avec les classes de base de données :  
  
-   [ODBC : bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
-   [ODBC : configuration d’une source de données ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)  
  
-   [ODBC : appel direct de fonctions API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base ODBC](../../data/odbc/odbc-basics.md)   
 [Administrateur ODBC](../../data/odbc/odbc-administrator.md)