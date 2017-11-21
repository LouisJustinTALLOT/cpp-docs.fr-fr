---
title: "Classe Platform::Collections :: vectorviewiterator | Documents Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
dev_langs: C++
helpviewer_keywords: VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 9c7d0c53464a000f74a4e552694e40af9d201992
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections::VectorViewIterator, classe
Fournit un itérateur Standard Template Library pour les objets dérivés de l’exécution de Windows`IVectorView` interface.  
  
 `ViewVectorIterator` est un itérateur de proxy qui stocke des éléments de type `VectorProxy<T>`. Toutefois, l'objet proxy n'est presque jamais visible par le code utilisateur. Pour plus d'informations, consultez [Collections (C++/CX)](../cppcx/collections-c-cx.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename T>  
class VectorViewIterator;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Typename de la classe de modèle VectorViewIterator.  
  
### <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`difference_type`|Différence de pointeur (ptrdiff_t).|  
|`iterator_category`|Catégorie d'un itérateur à accès aléatoire (::std::random_access_iterator_tag).|  
|`pointer`|Pointeur vers un type interne requis pour l'implémentation de VectorViewIterator.|  
|`reference`|Référence à un type interne requis pour l'implémentation de VectorViewIterator.|  
|`value_type`|Nom de type `T` .|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[VectorViewIterator::VectorViewIterator](#ctor)|Initialise une nouvelle instance de la classe VectorViewIterator.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[VectorViewIterator::operator-, opérateur](#operator-minus)|Soustrait un nombre spécifié d'éléments de l'itérateur actuel en cédant un nouvel itérateur, ou un itérateur spécifié de l'itérateur actuel en cédant le nombre d'éléments entre les itérateurs.|  
|[VectorViewIterator::operator--, opérateur](#operator-decrement)|Décrémente le VectorViewIterator actif.|  
|[VectorViewIterator::operator!=, opérateur](#operator-inequality)|Indique si le VectorViewIterator actuel n'est pas égal à un VectorViewIterator spécifié.|  
|[VectorViewIterator::operator*, opérateur](#operator-dereference)|Récupère une référence à l'élément spécifié par le VectorViewIterator actif.|  
|[VectorViewIterator::operator\[\]](#operator-at)|Extrait une référence à l'élément qui est un offset spécifié de l'objet VectorViewIterator actuel.|  
|[VectorViewIterator::operator+, opérateur](#operator-plus)|Retourne un VectorIterator qui référence l'élément au décalage spécifié à partir du VectorViewIterator spécifié.|  
|[VectorViewIterator::operator++, opérateur](#operator-increment)|Incrémente l'objet VectorViewIterator actuel.|  
|[VectorViewIterator::operator+=, opérateur](#operator-plus-assign)|Incrémente le VectorViewIterator actuel par le décalage spécifié.|  
|[VectorViewIterator::operator<, opérateur](#operator-less-than)|Indique si le VectorViewIterator actif est inférieur à un VectorViewIterator spécifié.|  
|[VectorViewIterator::operator\<= (opérateur)](#operator-less-than-or-equals)|Indique si le VectorViewIterator actif est inférieur ou égal à un VectorViewIterator spécifié.|  
|[VectorViewIterator::operator-=, opérateur](#operator-minus-assign)|Décrémente le VectorViewIterator actif du décalage spécifié.|  
|[VectorViewIterator::operator==, opérateur](#operator-equality)|Indique si le VectorViewIterator actif est égal à un VectorViewIterator spécifié.|  
|[VectorViewIterator::operator>, opérateur](#operator-greater-than)|Indique si le VectorViewIterator actif est supérieur à un VectorViewIterator spécifié.|  
|[VectorViewIterator::operator->, opérateur](#operator-arrow)|Récupère l'adresse de l'élément référencé par le VectorViewIterator actif.|  
|[VectorViewIterator::operator>=, opérateur](#operator-greater-than-or-equals)|Indique si le VectorViewIterator actif est supérieur ou égal à un VectorViewIterator spécifié.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `VectorViewIterator`  
  
### <a name="requirements"></a>Spécifications  
 **En-tête :** collection.h  
  
 **Espace de noms :** Platform::Collections  

## <a name="operator-arrow"></a>VectorViewIterator::operator -&gt; (opérateur)
Récupère l'adresse de l'élément référencé par le VectorViewIterator actif.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
Detail::ArrowProxy<T> operator->() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur de l’élément référencé par le VectorViewIterator actif.  
  
 Le type de la valeur de retour est un type interne non spécifié nécessaire pour l’implémentation de cet opérateur.  
  


## <a name="operator-decrement"></a>VectorViewIterator::operator--(opérateur)
Décrémente le VectorViewIterator actif.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
VectorViewIterator& operator--();  
VectorViewIterator operator--(int);  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La première syntaxe décrémente l’objet VectorViewIterator actif, puis le retourne. La deuxième syntaxe retourne une copie de l’objet VectorViewIterator actif, puis le décrémente.  
  
### <a name="remarks"></a>Remarques  
 La première syntaxe VectorViewIterator prédécrémente l’objet VectorViewIterator actif.  
  
 La deuxième syntaxe postdécrémente l’objet VectorViewIterator actif. Le `int` type dans la deuxième syntaxe indique une opération de post-décrémentation, pas un opérande entier réel.  
  


## <a name="operator-dereference"></a>Opérateur de VectorViewIterator::operator
Récupère une référence à l'élément spécifié par le VectorViewIterator actif.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Élément spécifié par le VectorViewIterator actif.  
  


## <a name="operator-equality"></a>VectorViewIterator::operator == (opérateur)
Indique si le VectorViewIterator actif est égal à un VectorViewIterator spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator==(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `other`  
 Un autre VectorViewIterator.  
  
### <a name="return-value"></a>Valeur de retour  
 `true`Si le VectorViewIterator actif est égal à `other`; sinon, `false`.  
  


## <a name="operator-greater-than"></a>VectorViewIterator::operator&gt; (opérateur)
Indique si le VectorViewIterator actif est supérieur à un VectorViewIterator spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
bool operator>(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `other`  
 Un autre VectorViewIterator.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si le VectorViewIterator actif est supérieur à `other` ; sinon, `false`.  
  


## <a name="operator-greater-than-or-equals"></a>VectorViewIterator::operator&gt;= (opérateur)
Indique si l'objet VectorViewIterator actuel est supérieur ou égal au VectorViewIterator spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
bool operator>=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `other`  
 Un autre VectorViewIterator.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si le VectorViewIterator actif est supérieur ou égal à `other` ; sinon, `false`.  
  


## <a name="operator-increment"></a>VectorViewIterator::operator ++ (opérateur)
Incrémente l'objet VectorViewIterator actuel.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
VectorViewIterator& operator++();  
VectorViewIterator operator++(int);  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La première syntaxe incrémente l'objet VectorViewIterator actuel, puis le retourne. La deuxième syntaxe retourne une copie de l'objet VectorViewIterator actuel, puis l'incrémente.  
  
### <a name="remarks"></a>Remarques  
 La première syntaxe VectorViewIterator préincrémente l'objet VectorViewIterator actuel.  
  
 La deuxième syntaxe postincrémente l'objet VectorViewIterator actuel. Le type `int` dans la deuxième syntaxe n'indique pas un opérande entier réel mais une post-incrémentation.  
  


## <a name="operator-inequality"></a>VectorViewIterator::operator ! =, opérateur
Indique si le VectorViewIterator actuel n'est pas égal à un VectorViewIterator spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator!=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `other`  
 Un autre VectorViewIterator.  
  
### <a name="return-value"></a>Valeur de retour  
 `true`Si le VectorViewIterator actif n’est pas égal à `other`; sinon, `false`.  
  


## <a name="operator-less-than"></a>VectorViewIterator::operator&lt; (opérateur)
Indique si le VectorIterator actuel est inférieur au VectorIterator spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator<(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `other`  
 Autre objet VectorIterator.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si le VectorIterator actuel est inférieur à `other` ; sinon, `false`.  
  


## <a name="operator-less-than-or-equals"></a>VectorViewIterator::operator&lt;= (opérateur)
Indique si l'objet VectorIterator actuel est inférieur ou égal à un objet VectorIterator spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
bool operator<=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `other`  
 Autre objet VectorIterator.  
  
### <a name="return-value"></a>Valeur de retour  
 `true`Si le VectorIterator actif est inférieur ou égal à `other`; sinon, `false`.  
  


## <a name="operator-minus"></a>VectorViewIterator::operator-(opérateur)
Soustrait un nombre spécifié d'éléments de l'itérateur actuel en cédant un nouvel itérateur, ou un itérateur spécifié de l'itérateur actuel en cédant le nombre d'éléments entre les itérateurs.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
VectorViewIterator operator-(difference_type n) const;  
  
difference_type operator-(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `n`  
 Nombre d'éléments.  
  
 `other`  
 Un autre VectorViewIterator.  
  
### <a name="return-value"></a>Valeur de retour  
 La première syntaxe d'opérateur retourne un objet VectorViewIterator qui a un nombre inférieur d'éléments `n` par rapport à l'objet VectorViewIterator actuel. La deuxième syntaxe d'opérateur retourne le nombre d'éléments entre l'objet actuel et l'objet VectorViewIterator `other`.  
  


## <a name="operator-plus-equals"></a>VectorViewIterator::operator += (opérateur)
Incrémente le VectorViewIterator actuel par le décalage spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
VectorViewIterator& operator+=(difference_type n);  
```  
  
### <a name="parameters"></a>Paramètres  
 `n`  
 Déplacement d'un entier.  
  
### <a name="return-value"></a>Valeur de retour  
 VectorViewIterator mis à jour.  
  


## <a name="operator-plus"></a>VectorViewIterator::operator + (opérateur)
Retourne un VectorIterator qui référence l'élément au décalage spécifié à partir du VectorViewIterator spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
VectorViewIterator operator+(difference_type n) const;  
  
template <typename T>   
inline VectorViewIterator<T> operator+  
   (ptrdiff_t n,   
   const VectorViewIterator<T>& i);  
  
```  
  
### <a name="parameters"></a>Paramètres  
 `T`  
 Dans la deuxième syntaxe, typename du VectorViewIterator.  
  
 `n`  
 Déplacement d'un entier.  
  
 `i`  
 Dans la deuxième syntaxe, un VectorViewIterator.  
  
### <a name="return-value"></a>Valeur de retour  
 Dans la première syntaxe, VectorViewIterator qui fait référence à l’élément spécifié au décalage spécifié par rapport au VectorViewIterator actuel.  
  
 Dans la deuxième syntaxe, VectorViewIterator qui fait référence à l’élément au décalage spécifié à partir du début du paramètre `i`.  
  


## <a name="operator-minus-assign"></a>VectorViewIterator::operator-= (opérateur)
Décrémente l'objet VectorIterator actuel du décalage spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
VectorViewIterator& operator-=(difference_type n);  
```  
  
### <a name="parameters"></a>Paramètres  
 `n`  
 Déplacement d'un entier.  
  
### <a name="return-value"></a>Valeur de retour  
 Objet VectorIterator mis à jour.  
  


## <a name="operator-at"></a>VectorViewIterator::operator\[\]
Extrait une référence à l'élément qui est un offset spécifié de l'objet VectorViewIterator actuel.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference operator[](difference_type n) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `n`  
 Déplacement d'un entier.  
  
### <a name="return-value"></a>Valeur de retour  
 Élément qui est déplacé par les éléments `n` de l'objet VectorViewIterator actuel.  
  


## <a name="ctor"></a>VectorViewIterator::VectorViewIterator (constructeur)
Initialise une nouvelle instance de la classe VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
VectorViewIterator();  
  
explicit VectorViewIterator(  
   Windows::Foundation::Collections::IVectorView<T>^ v  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 `v`  
 Un IVectorView\<T > objet.  
  
### <a name="remarks"></a>Remarques  
 Le premier exemple de syntaxe est le constructeur par défaut. Le deuxième exemple de syntaxe est un constructeur explicite qui est utilisé pour construire un VectorViewIterator à partir d’un IVectorView\<T > objet.  
  

  
## <a name="see-also"></a>Voir aussi  
 [Plateforme Namespace](platform-namespace-c-cx.md)