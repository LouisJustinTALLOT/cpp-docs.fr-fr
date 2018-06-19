---
title: 'ODBC : Configuration d’une Source de données ODBC | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: 1cd03e6a-8d59-4eca-a8c6-1010582d5e67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 93b2158005b7cd31fc6a3710812d54a3968ee014
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089150"
---
# <a name="odbc-configuring-an-odbc-data-source"></a>ODBC : configuration d'une source de données ODBC
Pour utiliser un [source de données](../../data/odbc/data-source-odbc.md) avec une application que vous avez développés, vous devez utiliser l’administrateur ODBC pour la configurer. L’administrateur ODBC assure le suivi des sources de données disponibles et leurs informations de connexion dans le Registre Windows. Utilisez l’administrateur ODBC pour ajouter, modifier et supprimer des sources de données dans le **des Sources de données** boîte de dialogue et d’ajouter et supprimer des pilotes ODBC.  
  
> [!NOTE]
>  Ces informations s’appliquent lorsque vous utilisez les classes de données Access objet DAO (MFC) pour accéder à ODBC et lorsque vous utilisez les classes ODBC MFC.  
  
 Administrateur ODBC est automatiquement installé avec la prise en charge de la base de données de la bibliothèque Microsoft Foundation Classes (MFC). Pour plus d’informations sur le programme Administrateur ODBC, consultez [administrateur ODBC](../../data/odbc/odbc-administrator.md) et le système d’aide ODBC API Reference en ligne.  
  
 Pour plus d’informations sur la façon d’écrire des programmes d’installation ODBC et d’Administration pour les applications de base de données MFC,[Technical Note 48](../../mfc/tn048-writing-odbc-setup-and-administration-programs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base ODBC](../../data/odbc/odbc-basics.md)   
 [ODBC : appel direct de fonctions API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)