---
title: CRowset::Insert | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset<TAccessor>.Insert
- CRowset.Insert
- CRowset<TAccessor>.Insert
- CRowset<TAccessor>::Insert
- ATL::CRowset<TAccessor>::Insert
- ATL.CRowset.Insert
- CRowset::Insert
- ATL::CRowset::Insert
dev_langs:
- C++
helpviewer_keywords:
- Insert method
ms.assetid: 6a64a1c3-10ac-4296-8685-0fd6fe63a13b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 44dddd6f3da835744463a9a95c44aa224d29d626
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098444"
---
# <a name="crowsetinsert"></a>CRowset::Insert
Crée et initialise une nouvelle ligne à l’aide des données à partir de l’accesseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Insert(int nAccessor = 0,   
   bool bGetHRow = false) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nAccessor`  
 [in] Le numéro de l’accesseur à utiliser pour insérer les données.  
  
 *bGetHRow*  
 [in] Indique si le handle de la ligne insérée est récupéré.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard.  
  
## <a name="remarks"></a>Notes  
 Cette méthode requiert l’interface facultative `IRowsetChange`, qui ne peut pas être pris en charge sur tous les fournisseurs ; si c’est le cas, la méthode retourne **E_NOINTERFACE**. Vous devez également définir **DBPROP_IRowsetChange** à `VARIANT_TRUE` avant d’appeler **ouvrir** sur la table ou d’une commande qui contient l’ensemble de lignes.  
  
 INSERT peut échouer si une ou plusieurs colonnes n’est pas accessible en écriture. Modifier le mappage de votre curseur pour corriger ce problème.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment accéder à une source de données via un ensemble de lignes, puis insérez une chaîne à l’aide d’une table dans cet ensemble de lignes.  
  
 Commencez par créer une classe de table en insérant un nouvel objet ATL dans votre projet. Par exemple, cliquez sur le projet dans le volet espace de travail et sélectionnez **nouvel objet ATL**. À partir de la **accès aux données** catégorie, sélectionnez **consommateur**. Créer un objet du consommateur de type **Table**. (En sélectionnant **Table** crée un ensemble de lignes directement à partir de la table ; sélection **commande** crée un ensemble de lignes via une commande SQL.) Sélectionnez une source de données, en spécifiant une table permettant d’accéder à cette source de données. Si vous appelez votre objet consommateur **CCustomerTable**, vous implémentez ensuite votre code d’insertion comme suit :  
  
 [!code-cpp[NVC_OLEDB_Consumer#10](../../data/oledb/codesnippet/cpp/crowset-insert_1.cpp)]  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CRowset, classe](../../data/oledb/crowset-class.md)