---
title: Activation et désactivation des Services pour un fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c9b255e715a635494e3acc34124871e90ceca8f7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055370"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Activation et désactivation de services pour un fournisseur

Des services OLE DB peuvent être activées ou désactivées par défaut pour toutes les applications qui accèdent à un seul fournisseur. Cela s’effectue en ajoutant une entrée de Registre OLEDB_SERVICES sous le CLSID du fournisseur, avec un `DWORD` valeur spécifiant les services pour activer ou désactiver, comme illustré dans le tableau suivant.

|Services activés par défaut|Valeur de mot clé|
|------------------------------|-------------------|
|Tous les services (par défaut)|0xFFFFFFFF|
|Tous sauf le regroupement et l’inscription automatique|0xFFFFFFFE|
|Tout sauf le curseur Client|0xfffffffb|
|Tous sauf le regroupement, l’inscription automatique et le curseur Client|0xfffffff0|
|Aucun service|0x00000000|
|Aucune agrégation, tous les services désactivés|\<clé manquante >|

## <a name="see-also"></a>Voir aussi

[Activation et désactivation des services OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)