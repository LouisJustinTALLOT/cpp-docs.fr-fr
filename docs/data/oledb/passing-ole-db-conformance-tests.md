---
title: Passage des Tests de compatibilité OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0288e1517bf89ec6ff8a2067311c3641d8d7113c
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340914"
---
# <a name="passing-ole-db-conformance-tests"></a>Tests de compatibilité OLE DB
Pour rendre les fournisseurs plus cohérente, le Data Access SDK fournit un ensemble de tests de compatibilité OLE DB. Les tests vérifient tous les aspects de votre fournisseur et vous donnent l’assurance raisonnable que votre fournisseur fonctionnera normalement. Vous pouvez trouver les tests de compatibilité OLE DB sur le Microsoft Data Access SDK. Cette section se concentre sur ce que vous devez faire pour passer les tests de compatibilité. Pour plus d’informations sur l’exécution de tests de compatibilité OLE DB, consultez le Kit de développement.  
  
## <a name="running-the-conformance-tests"></a>Les Tests de compatibilité en cours d’exécution  
 Dans Visual C++ 6.0, les modèles du fournisseur OLE DB ajouté un nombre de fonctions de raccordement pour vous permettent de vérifier les valeurs et propriétés. La plupart de ces fonctions ont été ajoutée en réponse aux tests de compatibilité.  
  
> [!NOTE]
>  Vous devez ajouter plusieurs fonctions de validation de votre fournisseur pour passer les tests de compatibilité OLE DB.  
  
 Ce fournisseur requiert deux routines de validation. La première routine, `CRowsetImpl::ValidateCommandID`, fait partie de votre classe rowset. Elle est appelée lors de la création de l’ensemble de lignes par les modèles du fournisseur. L’exemple utilise cette routine pour indiquer aux consommateurs qu’il ne prend pas en charge les index. Le premier appel consiste à `CRowsetImpl::ValidateCommandID` (Notez que le fournisseur utilise le `_RowsetBaseClass` typedef ajouté dans la table d’interface pour `CMyProviderRowset` dans [prise en charge de fournisseur de signets](../../data/oledb/provider-support-for-bookmarks.md), de sorte que vous n’êtes pas obligé de taper une longue ligne du modèle arguments). Ensuite, retournez DB_E_NOINDEX si le paramètre d’index n’est pas NULL (cela indique que le consommateur souhaite utiliser un index). Pour plus d’informations sur les ID de commande, consultez la spécification OLE DB et recherchez `IOpenRowset::OpenRowset`.  
  
 Le code suivant est le `ValidateCommandID` routine de validation :  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
// Class: CMyProviderRowset   
  
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
  
 Le modèles du fournisseur appellent la `OnPropertyChanged` méthode chaque fois qu’un utilisateur modifie une propriété sur le `DBPROPSET_ROWSET` groupe. Si vous souhaitez gérer des propriétés pour d’autres groupes, ajoutez-les à l’objet approprié (autrement dit, `DBPROPSET_SESSION` vérifications aller dans le `CMyProviderSession` classe).  
  
 Le code vérifie tout d’abord si la propriété est liée à un autre. Si la propriété est chaînée, il affecte la `DBPROP_BOOKMARKS` True à la propriété. Annexe C de la spécification OLE DB contient des informations sur les propriétés. Ces informations vous indique également si la propriété est chaînée à un autre.  
  
 Vous pourriez également ajouter le `IsValidValue` routine à votre code. L’appel de modèles `IsValidValue` lorsque vous tentez de définir une propriété. Vous devez remplacer cette méthode si vous avez besoin d’un traitement supplémentaire lors de la définition d’une valeur de propriété. Vous pouvez avoir une des méthodes suivantes pour chaque jeu de propriétés.  
  
## <a name="threading-issues"></a>Problèmes liés aux threads  
 Par défaut, l’Assistant fournisseur OLE DB dans l’Assistant fournisseur OLE DB ATL génère du code pour le fournisseur de s’exécuter dans un modèle de cloisonnement. Si vous essayez d’exécuter ce code avec les tests de compatibilité, vous obtenez des échecs. Ceci est le fait que Ltm.exe, l’outil utilisé pour exécuter les tests de compatibilité OLE DB, valeurs par défaut pour libérer de thread. Assistant fournisseur OLE DB code par défaut, le modèle de cloisonnement pour les performances et facilité d’utilisation.  
  
 Pour corriger ce problème, vous pouvez modifier LTM ou modifier le fournisseur.  
  
#### <a name="to-change-ltm-to-run-in-apartment-threaded-mode"></a>Pour modifier LTM à exécuter dans le cloisonnement mode thread  
  
1.  Dans le menu principal de LTM, cliquez sur **outils**, puis cliquez sur **Options**.  
  
2.  Sur le **général** , modifiez le modèle de thread à partir de **thread libre** à **Apartment Threaded**.  
  
 Pour modifier votre fournisseur pour s’exécuter en mode thread libre :  
  
-   Dans votre projet de fournisseur, recherchez toutes les instances de `CComSingleThreadModel` et remplacez-la par `CComMultiThreadModel`, qui doit être dans les en-têtes d’ensemble de lignes, de session et de source de données.  
  
-   Dans le fichier .rgs, modifiez le modèle de thread à partir de **cloisonnement** à **les deux**.  
  
-   Programmation multithread gratuitement (autrement dit, un verrou sur les écritures) de règles de programmation correctes de suivi.  
  
## <a name="see-also"></a>Voir aussi  
 [Techniques avancées du fournisseur](../../data/oledb/advanced-provider-techniques.md)