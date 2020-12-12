---
description: 'En savoir plus sur : interfaces de l’objet de commande'
title: Interfaces de l'objet Command
ms.date: 10/24/2018
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
ms.openlocfilehash: 07dce6a71e7afd3a47c63942d48dd78d758103f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307520"
---
# <a name="command-object-interfaces"></a>Interfaces de l'objet Command

L’objet Command utilise l' `IAccessor` interface pour spécifier des liaisons de paramètres. Le consommateur appelle `IAccessor::CreateAccessor` , en lui passant un tableau de `DBBINDING` structures. `DBBINDING` contient des informations sur les liaisons de colonne (telles que le type et la longueur). Le fournisseur reçoit les structures et détermine la façon dont les données doivent être transférées, ainsi que les conversions nécessaires.

L' `ICommandText` interface fournit un moyen de spécifier une commande de texte. L' `ICommandProperties` interface gère toutes les propriétés de commande.

## <a name="see-also"></a>Voir aussi

[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
