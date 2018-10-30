---
title: Interfaces de l’objet de commande | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: f5d09e5794b66895d4bfd6a12fe7b0e1dbeeea7f
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216329"
---
# <a name="command-object-interfaces"></a>Interfaces de l'objet de commande

L’objet de commande utilise le `IAccessor` interface pour spécifier les liaisons de paramètres. Le consommateur appelle `IAccessor::CreateAccessor`, en lui passant un tableau de `DBBINDING` structures. `DBBINDING` contient des informations sur les liaisons de colonne (par exemple, le type et la longueur). Le fournisseur reçoit les structures et détermine comment les données doivent être transférées et si les conversions sont nécessaires.

Le `ICommandText` interface fournit un moyen de spécifier une commande de texte. Le `ICommandProperties` interface gère toutes les propriétés de commande.

## <a name="see-also"></a>Voir aussi

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
