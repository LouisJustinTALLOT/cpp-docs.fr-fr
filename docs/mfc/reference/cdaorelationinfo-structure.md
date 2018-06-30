---
title: Cdaorelationinfo, Structure | Documents Microsoft
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoRelationInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure [MFC]
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8887c9735b91c43e9dc43140df792841eecef5ed
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122606"
---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo, structure
Le `CDaoRelationInfo` structure contient des informations sur une relation définie entre les champs de deux tables dans un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
struct CDaoRelationInfo  
{  
    CDaoRelationInfo();                     // Constructor  
    CString m_strName;                      // Primary  
    CString m_strTable;                     // Primary  
    CString m_strForeignTable;              // Primary  
    long m_lAttributes;                     // Secondary  
    CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary  
    short m_nFields;                        // Secondary
    // Below the // Implementation comment:
    // Destructor, not otherwise documented  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
*m_strName*  
 Identifie l’objet de relation. Pour plus d’informations, consultez la rubrique « Nom de propriété » dans l’aide de DAO.  
  
 *m_strTable*  
 Noms de la table primaire de la relation.  
  
 *m_strForeignTable*  
 Noms de la table étrangère dans la relation. Une table étrangère est une table utilisée pour contenir des clés étrangères. En règle générale, vous utilisez une table étrangère pour établir ou appliquer l’intégrité référentielle. La table étrangère est généralement le côté « plusieurs » d’une relation un-à-plusieurs. Tables contenant des codes d’États américains ou canadiens provinces les commandes client sont des exemples de tables externes.  
  
 *m_lAttributes*  
 Contient des informations sur le type de relation. La valeur de ce membre peut être une des opérations suivantes :  
  
- **dbRelationUnique** relation est un à un.  
  
- **Pourriez** relation n’est pas appliquée (aucune intégrité référentielle).  
  
- **dbRelationInherited** relation existe dans une base de données non courante qui contient les deux tables attachées.  
  
- **dbRelationLeft** la relation est une jointure gauche. Une jointure externe gauche comprend tous les enregistrements de la première (gauche) de deux tables, même si aucune valeur correspondante pour les enregistrements de la seconde table (à droite).  
  
- **dbRelationRight** la relation est une jointure droite. Une jointure externe droite comprend tous les enregistrements de la deuxième (à droite) de deux tables, même si aucune valeur correspondante pour les enregistrements de la première table (gauche).  
  
- **dbRelationUpdateCascade** mises à jour seront produisent en cascade.  
  
- **dbRelationDeleteCascade** suppressions seront produisent en cascade.  
  
*m_pFieldInfos*  
 Un pointeur vers un tableau de [CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) structures. Le tableau contient un objet pour chaque champ dans la relation. Le `m_nFields` donnée membre donne le nombre d’éléments du tableau.  
  
*m_nFields*  
 Le nombre de `CDaoRelationFieldInfo` des objets dans le `m_pFieldInfos` membre de données.  
  
## <a name="remarks"></a>Notes  
 Les références aux principaux et secondaires ci-dessus indiquent la façon dont les informations sont retournées par la [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) fonction membre dans la classe `CDaoDatabase`.  
  
 Les objets de relation ne sont pas représentées par une classe MFC. Au lieu de cela, l’objet DAO sous-jacent d’un objet MFC de la `CDaoDatabase` classe maintient une collection d’objets relation : `CDaoDatabase` fournit les fonctions de membre pour accéder à certains éléments individuels d’informations sur la relation, ou vous peuvent y accéder à la fois avec un `CDaoRelationInfo` objet en appelant le `GetRelationInfo` fonction membre de l’objet conteneur de la base de données.  
  
 Les informations extraites par le [CDaoDatabase::GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) fonction membre est stockée dans un `CDaoRelationInfo` structure. `CDaoRelationInfo` définit également un `Dump` builds de la fonction membre en mode débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoRelationInfo` objet.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdao.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDaoRelationFieldInfo, structure](../../mfc/reference/cdaorelationfieldinfo-structure.md)
