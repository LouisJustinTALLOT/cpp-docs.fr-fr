---
title: Tests de compatibilité OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
ms.openlocfilehash: 7365176df314baf40ac1cc1ed53936598f05c79e
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265072"
---
# <a name="passing-ole-db-conformance-tests"></a>Tests de compatibilité OLE DB

Pour rendre les fournisseurs plus cohérente, le Data Access SDK fournit un ensemble de tests de compatibilité OLE DB. Les tests vérifient tous les aspects de votre fournisseur et vous donnent l’assurance raisonnable que votre fournisseur fonctionnera normalement. Vous pouvez trouver les tests de compatibilité OLE DB sur le Microsoft Data Access SDK. Cette section se concentre sur ce que vous devez faire pour passer les tests de compatibilité. Pour plus d’informations sur l’exécution de tests de compatibilité OLE DB, consultez le Kit de développement.

## <a name="running-the-conformance-tests"></a>Les Tests de compatibilité en cours d’exécution

Dans Visual C++ 6.0, les modèles du fournisseur OLE DB ajouté un nombre de fonctions de raccordement pour vous permettent de vérifier les valeurs et propriétés. La plupart de ces fonctions ont été ajoutée en réponse aux tests de compatibilité.

> [!NOTE]
> Vous devez ajouter plusieurs fonctions de validation de votre fournisseur pour passer les tests de compatibilité OLE DB.

Ce fournisseur requiert deux routines de validation. La première routine, `CRowsetImpl::ValidateCommandID`, fait partie de votre classe rowset. Elle est appelée lors de la création de l’ensemble de lignes par les modèles du fournisseur. L’exemple utilise cette routine pour indiquer aux consommateurs qu’il ne prend en charge les index. Le premier appel consiste à `CRowsetImpl::ValidateCommandID` (Notez que le fournisseur utilise le `_RowsetBaseClass` typedef ajouté dans la table d’interface pour `CCustomRowset` dans [prise en charge de fournisseur de signets](../../data/oledb/provider-support-for-bookmarks.md), de sorte que vous n’êtes pas obligé de taper une longue ligne du modèle arguments). Ensuite, retournez DB_E_NOINDEX si le paramètre d’index n’est pas NULL (cela indique que le consommateur souhaite utiliser un index). Pour plus d’informations sur les ID de commande, consultez la spécification OLE DB et recherchez `IOpenRowset::OpenRowset`.

Le code suivant est le `ValidateCommandID` routine de validation :

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H
// Class: CCustomRowset

HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)
{
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);
   if (hr != S_OK)
      return hr;

   if (pIndexID != NULL)
      return DB_E_NOINDEX;    // Doesn't support indexes

   return S_OK;
}
```

Le modèles du fournisseur appellent la `OnPropertyChanged` méthode chaque fois qu’un utilisateur modifie une propriété dans le groupe DBPROPSET_ROWSET. Si vous souhaitez gérer des propriétés pour d’autres groupes, ajoutez-les à l’objet approprié (autrement dit, les vérifications DBPROPSET_SESSION aller dans le `CCustomSession` classe).

Le code vérifie tout d’abord si la propriété est liée à un autre. Si la propriété est chaînée, il définit la propriété DBPROP_BOOKMARKS sur `True`. Annexe C de la spécification OLE DB contient des informations sur les propriétés. Ces informations vous indique également si la propriété est chaînée à un autre.

Vous pourriez également ajouter le `IsValidValue` routine à votre code. L’appel de modèles `IsValidValue` lorsque vous tentez de définir une propriété. Vous devez remplacer cette méthode si vous avez besoin d’un traitement supplémentaire lors de la définition d’une valeur de propriété. Vous pouvez avoir une des méthodes suivantes pour chaque jeu de propriétés.

## <a name="see-also"></a>Voir aussi

[Techniques avancées du fournisseur](../../data/oledb/advanced-provider-techniques.md)