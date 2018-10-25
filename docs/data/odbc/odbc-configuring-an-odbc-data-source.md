---
title: 'ODBC : Configuration d’une Source de données ODBC | Microsoft Docs'
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
ms.openlocfilehash: a9a0cd385596f62432f16b7e5abc4259a267dd76
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080310"
---
# <a name="odbc-configuring-an-odbc-data-source"></a>ODBC : configuration d'une source de données ODBC

Pour utiliser un [source de données](../../data/odbc/data-source-odbc.md) avec une application que vous avez développé, vous devez utiliser l’administrateur ODBC pour la configurer. L’administrateur ODBC assure le suivi des sources de données disponibles et leurs informations de connexion dans le Registre Windows. Utilisez l’administrateur ODBC pour ajouter, modifier et supprimer des sources de données dans le **des Sources de données** boîte de dialogue et d’ajouter et supprimer des pilotes ODBC.

> [!NOTE]
>  Ces informations s’appliquent lorsque vous utilisez des classes de données Access objet DAO (MFC) pour accéder à ODBC et lorsque vous utilisez des classes ODBC MFC.

Administrateur ODBC est automatiquement installé avec la prise en charge de la base de données de la bibliothèque Microsoft Foundation Classes (MFC). Pour plus d’informations sur le programme Administrateur ODBC, consultez [administrateur ODBC](../../data/odbc/odbc-administrator.md) et le système d’aide de référence d’API ODBC en ligne.

Pour plus d’informations sur la façon d’écrire des programmes d’installation ODBC et d’Administration pour les applications de base de données MFC,[Technical Note 48](../../mfc/tn048-writing-odbc-setup-and-administration-programs.md).

## <a name="see-also"></a>Voir aussi

[Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)<br/>
[ODBC : appel direct de fonctions API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)