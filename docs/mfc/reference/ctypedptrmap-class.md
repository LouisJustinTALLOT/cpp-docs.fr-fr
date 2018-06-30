---
title: CTypedPtrMap (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f312d7e829657f2cc9c7c41c65afad8d8f8b343
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121862"
---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap (classe)
Fournit un « wrapper » de type sécurisé pour les objets des classes de mappage de pointeur `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`et `CMapStringToPtr`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class BASE_CLASS, class KEY, class VALUE>  
class CTypedPtrMap : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>Paramètres  
 *BASE_CLASS*  
 Classe de base de la classe map de pointeurs typés ; doit être une classe de mappage de pointeur ( `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, ou `CMapStringToPtr`).  
  
 *KEY*  
 Classe de l’objet utilisé comme clé pour la carte.  
  
 *VALEUR*  
 Classe de l’objet stocké dans le mappage.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Obtient l’élément suivant pour une itération.|  
|[CTypedPtrMap::Lookup](#lookup)|Retourne un `KEY` basé sur un `VALUE`.|  
|[CTypedPtrMap::RemoveKey](#removekey)|Supprime un élément spécifié par une clé.|  
|[CTypedPtrMap::SetAt](#setat)|Insère un élément dans l’objet map. remplace un élément existant si une clé est trouvée.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[[] De CTypedPtrMap::operator](#operator_at)|Insère un élément dans le mappage.|  
  
## <a name="remarks"></a>Notes  
 Lorsque vous utilisez `CTypedPtrMap`, la fonctionnalité de vérification de type C++ vous aide à éliminer les erreurs provoquées par les types pointeur ne correspondent pas.  
  
 Étant donné que tous les `CTypedPtrMap` fonctions sont en ligne, l’utilisation de ce modèle n’affecte pas considérablement la taille ou la vitesse de votre code.  
  
 Pour plus d’informations sur l’utilisation de `CTypedPtrMap`, consultez les articles [Collections](../../mfc/collections.md) et [Classes basées sur le modèle](../../mfc/template-based-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `BASE_CLASS`  
  
 `CTypedPtrMap`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxtempl.h  
  
##  <a name="getnextassoc"></a>  CTypedPtrMap::GetNextAssoc  
 Récupère l’élément de mappage à `rNextPosition`, puis met à jour `rNextPosition` pour faire référence à l’élément suivant dans la carte.  
  
```  
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *rPosition*  
 Spécifie une référence à une valeur POSITION renvoyée par une précédente `GetNextAssoc` ou `BASE_CLASS` **:: GetStartPosition** appeler.  
  
 *KEY*  
 Paramètre de modèle qui spécifie le type des clés de la carte.  
  
 *rKey*  
 Spécifie la clé retournée de l’élément récupéré.  
  
 *VALEUR*  
 Paramètre de modèle qui spécifie le type des valeurs de la carte.  
  
 *rValue*  
 Spécifie la valeur retournée de l’élément récupéré.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est particulièrement utile pour l’itération au sein de tous les éléments dans le mappage. Notez que la séquence de position n’est pas nécessairement identique à la séquence de la valeur de clé.  
  
 Si l’élément récupéré est le dernier dans le mappage, puis la nouvelle valeur de `rNextPosition` est définie sur NULL.  
  
 Cette fonction inline s’appelle `BASE_CLASS` **:: GetNextAssoc**.  
  
##  <a name="lookup"></a>  CTypedPtrMap::Lookup  
 `Lookup` utilise un algorithme de hachage pour trouver rapidement l’élément de carte avec une clé qui correspond exactement.  
  
```  
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *BASE_CLASS*  
 Paramètre de modèle en spécifiant la classe de base de la classe de cette carte.  
  
 *key*  
 La clé de l’élément à rechercher.  
  
 *VALEUR*  
 Paramètre de modèle qui spécifie le type des valeurs stockées dans ce mappage.  
  
 *rValue*  
 Spécifie la valeur retournée de l’élément récupéré.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément a été trouvé ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction inline s’appelle `BASE_CLASS` **:: recherche**.  
  
##  <a name="operator_at"></a>  [] De CTypedPtrMap::operator  
 Cet opérateur peut être utilisé uniquement sur le côté gauche d’une instruction d’assignation (une l-value).  
  
```  
VALUE& operator[ ](base_class ::base_arg_key key);
```  
  
### <a name="parameters"></a>Paramètres  
 *VALEUR*  
 Paramètre de modèle qui spécifie le type des valeurs stockées dans ce mappage.  
  
 *BASE_CLASS*  
 Paramètre de modèle en spécifiant la classe de base de la classe de cette carte.  
  
 *key*  
 La clé de l’élément de recherche ou la création du mappage.  
  
### <a name="remarks"></a>Notes  
 S’il n’existe aucun élément de carte avec la clé spécifiée, un nouvel élément est créé. Aucun (r-value) « droite » n’est équivalent à cet opérateur, car il est possible qu’une clé peut être introuvable dans le mappage. Utilisez le `Lookup` fonction membre pour l’extraction d’un élément.  
  
##  <a name="removekey"></a>  CTypedPtrMap::RemoveKey  
 Cette fonction membre appelle `BASE_CLASS` **:: RemoveKey**.  
  
```  
BOOL RemoveKey(KEY key);
```  
  
### <a name="parameters"></a>Paramètres  
 *KEY*  
 Paramètre de modèle qui spécifie le type des clés de la carte.  
  
 *key*  
 Clé de l’élément à supprimer.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’entrée a été trouvée et supprimée avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus de la section Notes, consultez [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).  
  
##  <a name="setat"></a>  CTypedPtrMap::SetAt  
 Cette fonction membre appelle `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(KEY key, VALUE newValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *KEY*  
 Paramètre de modèle qui spécifie le type des clés de la carte.  
  
 *key*  
 Spécifie la valeur de clé de la nouvelle valeur.  
  
 *nouvelle valeur*  
 Spécifie le pointeur d’objet qui est la valeur du nouvel élément.  
  
### <a name="remarks"></a>Notes  
 Pour plus de la section Notes, consultez [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC COLLECT](../../visual-cpp-samples.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)   
 [Classe de CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)   
 [Classe de CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)   
 [CMapStringToPtr, classe](../../mfc/reference/cmapstringtoptr-class.md)
