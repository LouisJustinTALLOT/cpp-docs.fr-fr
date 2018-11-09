---
title: Activation et désactivation de services pour un fournisseur
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: 23579b9561356e95d315c0fbe47132208753afa8
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265124"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Activation et désactivation de services pour un fournisseur

Des services OLE DB peuvent être activées ou désactivées par défaut pour toutes les applications qui accèdent à un seul fournisseur. Pour cela, vous devez ajouter une entrée de Registre OLEDB_SERVICES sous le CLSID du fournisseur, avec une valeur DWORD spécifiant les services pour activer ou désactiver, comme illustré dans le tableau suivant.

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