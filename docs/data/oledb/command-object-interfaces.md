---
title: Interfaces de l’objet de commande | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8176bad2921edd22edaab1688e38bc7de275b0bb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074798"
---
# <a name="command-object-interfaces"></a>Interfaces de l'objet de commande

L’objet de commande utilise le `IAccessor` interface pour spécifier les liaisons de paramètres. Le consommateur appelle `IAccessor::CreateAccessor`, en lui passant un tableau de `DBBINDING` structures. `DBBINDING` contient des informations sur les liaisons de colonne (par exemple, le type et la longueur). Le fournisseur reçoit les structures et détermine comment les données doivent être transférées et si les conversions sont nécessaires.

Le `ICommandText` interface fournit un moyen de spécifier une commande de texte. Le `ICommandProperties` interface gère toutes les propriétés de commande.

## <a name="see-also"></a>Voir aussi

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)