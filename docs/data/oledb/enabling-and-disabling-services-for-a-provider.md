---
title: Activation et désactivation de services pour un fournisseur
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: d91f08accf1a8be69f63d6bbcaa4c620d68c1077
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033029"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Activation et désactivation de services pour un fournisseur

Des services OLE DB peuvent être activées ou désactivées par défaut pour toutes les applications qui accèdent à un seul fournisseur. Pour cela, vous devez ajouter une entrée de Registre OLEDB_SERVICES sous le CLSID du fournisseur, avec une valeur DWORD spécifiant les services pour activer ou désactiver, comme illustré dans le tableau suivant.

|Services activés par défaut|Valeur de mot clé|
|------------------------------|-------------------|
|Tous les services (par défaut)|0xffffffff|
|Tous sauf le regroupement et l’inscription automatique|0xfffffffe|
|Tout sauf le curseur Client|0xfffffffb|
|Tous sauf le regroupement, l’inscription automatique et le curseur Client|0xfffffff0|
|Aucun service|0x00000000|
|Aucune agrégation, tous les services désactivés|\<clé manquante >|

## <a name="see-also"></a>Voir aussi

[Activation et désactivation des services OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)