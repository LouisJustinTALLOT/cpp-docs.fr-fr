---
title: 'Classe Platform::Collections :: inputiterator | Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
dev_langs:
- C++
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fbd80f649b27bcb3af720871d6d1378f5fe220c8
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208482"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator, classe
Fournit un InputIterator de bibliothèque de modèle Standard pour les collections dérivées de l’exécution de Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename X>  
class InputIterator;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `X`  
 Nom de type de la classe de modèle InputIterator.  
  
### <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`difference_type`|Différence de pointeur (ptrdiff_t).|  
|`iterator_category`|Catégorie d’un itérateur d’entrée (:: std::input_iterator_tag).|  
|`pointer`|Pointeur vers un `const X`|  
|`reference`|Référence à un `const X`|  
|`value_type`|Nom de type `X` .|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[InputIterator::InputIterator](#ctor)|Initialise une nouvelle instance de la classe InputIterator.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[InputIterator::operator!=, opérateur](#operator-inequality)|Indique si l'InputIterator actif n'est pas égal à un InputIterator spécifié.|  
|[InputIterator::operator*, opérateur](#operator-decrement)|Récupère une référence à l’élément spécifié par l’InputIterator actif.|  
|[InputIterator::operator++, opérateur](#operator-increment)|Incrémente l'objet InputIterator actuel.|  
|[InputIterator::operator==, opérateur](#operator-equality)|Indique si l'InputIterator actif est égal à un InputIterator spécifié.|  
|[InputIterator::operator->, opérateur](#operator-arrow)|Récupère l’adresse de l’élément référencé par l’InputIterator actif.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `InputIterator`  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** collection.h  
  
 **Espace de noms :** Platform::Collections  

## <a name="ctor"></a>  InputIterator::InputIterator (constructeur)
Initialise une nouvelle instance de la classe InputIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
InputIterator();  
explicit InputIterator(Windows::Foundation::Collections<X>^ iter);  
```  
  
### <a name="parameters"></a>Paramètres  
 `iter`  
 Objet itérateur.  
  


## <a name="operator-arrow"></a>  InputIterator::operator -&gt; opérateur
Récupère l’adresse de l’élément spécifié par l’objet InputIterator actif.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
pointer operator->() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Adresse de l’élément spécifié par l’objet InputIterator actif.  
  


## <a name="operator-dereference"></a>  InputIterator::operator\* opérateur
Récupère une référence à l’élément spécifié par l’InputIterator actif.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Élément spécifié par l’InputIterator actif.  
  


## <a name="operator-equality"></a>  InputIterator::operator ==, opérateur
Indique si l'InputIterator actif est égal à un InputIterator spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator== (const InputIterator& other) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `other`  
 Autre InputIterator.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si l'InputIterator actif est égal à `other` ; sinon, `false`.  
  


## <a name="operator-increment"></a>  InputIterator::operator ++ (opérateur)
Incrémente l'objet InputIterator actuel.  
  
### <a name="syntax"></a>Syntaxe  
  
```    
InputIterator& operator++();   
InputIterator operator++(int);  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La première syntaxe incrémente l'objet InputIterator actuel puis le retourne. La deuxième syntaxe retourne une copie de l'objet InputIterator actuel, puis incrémente l'objet InputIterator actuel.  
  
### <a name="remarks"></a>Notes  
 La première syntaxe InputIterator préincrémente l'objet InputIterator actuel.  
  
 La deuxième syntaxe postincrémente l'objet InputIterator actuel. Le type `int` dans la deuxième syntaxe n'indique pas un opérande entier réel mais une post-incrémentation.  
  


## <a name="operator-inequality"></a>  InputIterator::operator ! =, opérateur
Indique si l'InputIterator actif n'est pas égal à un InputIterator spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator!=(const InputIterator& other) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `other`  
 Autre InputIterator.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si l'InputIterator actif n'est pas égal à `other` ; sinon, `false`.   

  
## <a name="see-also"></a>Voir aussi  
 [Plateforme Namespace](platform-namespace-c-cx.md)