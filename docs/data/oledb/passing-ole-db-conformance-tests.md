---
description: 'En savoir plus sur : transmission de OLE DB tests de conformité'
title: Tests de compatibilité OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
ms.openlocfilehash: d2a5b788b3a118293800b02a9383fbde9845cfa5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286721"
---
# <a name="passing-ole-db-conformance-tests"></a>Tests de compatibilité OLE DB

Pour rendre les fournisseurs plus cohérents, le kit de développement logiciel (SDK) d’accès aux données fournit un ensemble de tests de conformité OLE DB. Les tests vérifient tous les aspects de votre fournisseur et vous garantissent que votre fournisseur fonctionne comme prévu. Vous pouvez trouver les tests de conformité OLE DB sur le kit de développement logiciel (SDK) Microsoft Data Access. Cette section se concentre sur les tâches à effectuer pour réussir les tests de conformité. Pour plus d’informations sur l’exécution des tests de conformité OLE DB, consultez le kit de développement logiciel (SDK).

## <a name="running-the-conformance-tests"></a>Exécution des tests de conformité

Dans Visual C++ 6,0, les modèles de fournisseur d’OLE DB ajoutaient un certain nombre de fonctions de raccordement pour vous permettre de vérifier les valeurs et les propriétés. La plupart de ces fonctions ont été ajoutées en réponse aux tests de conformité.

> [!NOTE]
> Vous devez ajouter plusieurs fonctions de validation pour que votre fournisseur passe les tests de conformité OLE DB.

Ce fournisseur requiert deux routines de validation. La première routine, `CRowsetImpl::ValidateCommandID` , fait partie de votre classe rowset. Elle est appelée pendant la création de l’ensemble de lignes par les modèles du fournisseur. L’exemple utilise cette routine pour indiquer aux consommateurs qu’il ne prend pas en charge les index. Le premier appel est à `CRowsetImpl::ValidateCommandID` (Notez que le fournisseur utilise le `_RowsetBaseClass` typedef ajouté dans le mappage d’interface pour la `CCustomRowset` [prise en charge des signets](../../data/oledb/provider-support-for-bookmarks.md)par le fournisseur. vous n’avez donc pas besoin de taper cette longue ligne d’arguments template). Ensuite, retournez DB_E_NOINDEX si le paramètre d’index n’est pas NULL (cela indique que le consommateur souhaite utiliser un index sur nous). Pour plus d’informations sur les ID de commande, consultez la spécification OLE DB et recherchez `IOpenRowset::OpenRowset` .

Le code suivant est la `ValidateCommandID` routine de validation :

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

Les modèles de fournisseur appellent la `OnPropertyChanged` méthode chaque fois qu’un utilisateur modifie une propriété sur le groupe de DBPROPSET_ROWSET. Si vous souhaitez gérer les propriétés d’autres groupes, vous devez les ajouter à l’objet approprié (autrement dit, DBPROPSET_SESSION les contrôles sont placés dans la `CCustomSession` classe).

Le code commence par vérifier si la propriété est liée à une autre. Si la propriété est chaînée, elle affecte à la propriété DBPROP_BOOKMARKS la valeur `True` . L’annexe C de la spécification OLE DB contient des informations sur les propriétés. Ces informations vous indiquent également si la propriété est chaînée à une autre.

Vous pouvez également ajouter la `IsValidValue` routine à votre code. Les modèles appellent `IsValidValue` lors de la tentative de définition d’une propriété. Vous substituez cette méthode si vous avez besoin d’un traitement supplémentaire lors de la définition d’une valeur de propriété. Vous pouvez avoir l’une de ces méthodes pour chaque jeu de propriétés.

## <a name="see-also"></a>Voir aussi

[Techniques avancées du fournisseur](../../data/oledb/advanced-provider-techniques.md)
