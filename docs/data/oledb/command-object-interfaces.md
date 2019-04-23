---
title: Interfaces de l'objet de commande
ms.date: 10/24/2018
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
ms.openlocfilehash: 755c44cf8d0cb5bf5066197bfd0ead3e0f25e1f9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032399"
---
# <a name="command-object-interfaces"></a>Interfaces de l'objet de commande

L’objet de commande utilise le `IAccessor` interface pour spécifier les liaisons de paramètres. Le consommateur appelle `IAccessor::CreateAccessor`, en lui passant un tableau de `DBBINDING` structures. `DBBINDING` contient des informations sur les liaisons de colonne (par exemple, le type et la longueur). Le fournisseur reçoit les structures et détermine comment les données doivent être transférées et si les conversions sont nécessaires.

Le `ICommandText` interface fournit un moyen de spécifier une commande de texte. Le `ICommandProperties` interface gère toutes les propriétés de commande.

## <a name="see-also"></a>Voir aussi

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
