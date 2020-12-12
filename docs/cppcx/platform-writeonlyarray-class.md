---
description: 'En savoir plus sur : classe Platform :: WriteOnlyArray'
title: Platform::WriteOnlyArray (classe)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
helpviewer_keywords:
- Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
ms.openlocfilehash: cddbe0d3823ba7b9751bd60844d9ce699546b804
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307767"
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray (classe)

Représente un tableau unidimensionnel utilisé comme paramètre d'entrée lorsque l'appelant transmet un tableau à remplir pour la méthode.

Cette classe ref est déclarée comme privée dans vccorlib.h. Par conséquent, elle n'est pas émise dans les métadonnées et est uniquement consommable à partir de C++. Cette classe est prévue uniquement pour être utilisée comme paramètre d'entrée qui accepte un tableau que l'appelant a alloué. Elle n'est pas constructible à partir du code utilisateur. Il permet à la méthode C++ d'écrire directement dans ce tableau, un modèle appelé modèle *FillArray* . Pour plus d’informations, consultez [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="syntax"></a>Syntaxe

```cpp
private ref class WriteOnlyArray<T, 1>
```

### <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

Ces méthodes offrent une accessibilité interne, c'est-à-dire qu'elles ne sont accessibles que dans l'application ou le composant C++.

|Nom|Description|
|----------|-----------------|
|[WriteOnlyArray :: Begin](#begin)|Itérateur qui pointe vers le premier élément du tableau.|
|[WriteOnlyArray ::D ATA](#data)|Pointeur vers le tampon de données.|
|[WriteOnlyArray :: fin](#end)|Itérateur qui pointe vers un élément au-delà du dernier élément du tableau.|
|[WriteOnlyArray :: FastPass](#fastpass)|Indique si le tableau peut utiliser le mécanisme FastPass, qui est une optimisation exécutée en toute transparence par le système. N'utilisez pas cela dans votre code|
|[WriteOnlyArray :: length](#length)|Retourne le nombre d'éléments du tableau.|
|[WriteOnlyArray :: Set](#set)|Définit l'élément spécifié sur la valeur spécifiée.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`WriteOnlyArray`

### <a name="requirements"></a>Spécifications

Option du compilateur : **/ZW**

**Métadonnées :** platform.winmd

**Espace de noms :** Platform

## <a name="writeonlyarraybegin-method"></a><a name="begin"></a> WriteOnlyArray :: Begin, méthode

Retourne un pointeur désignant le premier élément du tableau.

### <a name="syntax"></a>Syntaxe

```cpp
T* begin() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur désignant le premier élément du tableau.

### <a name="remarks"></a>Notes

Cet itérateur peut être utilisé avec les algorithmes STL tels que `std::sort` pour exécuter des opérations sur les élément du tableau.

## <a name="writeonlyarraydata-property"></a><a name="data"></a> WriteOnlyArray : propriété ATA :D

Pointeur vers le tampon de données.

### <a name="syntax"></a>Syntaxe

```cpp
property T* Data{
   T* get() const;
}
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers les octets bruts de tableau.

## <a name="writeonlyarrayend-method"></a><a name="end"></a> WriteOnlyArray :: end, méthode

Retourne un pointeur sur un point suivant au-delà du dernier élément du tableau.

### <a name="syntax"></a>Syntaxe

```cpp
T* end() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur de pointeur sur un point suivant au-delà du dernier élément du tableau.

### <a name="remarks"></a>Notes

Cet itérateur peut être utilisé avec les algorithmes STL pour exécuter des opérations telles que `std::sort` sur les éléments de tableau.

## <a name="writeonlyarrayfastpass-property"></a><a name="fastpass"></a> WriteOnlyArray :: FastPass, propriété

Indique si l'optimisation interne FastPass peut être exécutée. Non destiné à être utilisé par le code utilisateur.

### <a name="syntax"></a>Syntaxe

```cpp
property bool FastPass{
   bool get() const;
}
```

### <a name="return-value"></a>Valeur de retour

Valeur booléenne qui indique si le tableau est FastPass.

## <a name="writeonlyarrayget-method"></a><a name="get"></a> WriteOnlyArray :: méthode d’extraction

Retourne l'élément à l'index spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
T& get(unsigned int indexArg) const;
```

### <a name="parameters"></a>Paramètres

*indexArg*<br/>
Index à utiliser.

### <a name="return-value"></a>Valeur renvoyée

## <a name="writeonlyarraylength-property"></a><a name="length"></a> WriteOnlyArray :: Length, propriété

Retourne le nombre d'éléments du tableau alloué par l'appelant.

### <a name="syntax"></a>Syntaxe

```cpp
property unsigned int Length{
   unsigned int get() const;
}
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans le tableau.

## <a name="writeonlyarrayset-function"></a><a name="set"></a> WriteOnlyArray :: Set, fonction

Définit la valeur spécifiée à l'index spécifié dans le tableau.

### <a name="syntax"></a>Syntaxe

```cpp
T& set(
   unsigned int indexArg,
   T valueArg);
```

### <a name="parameters"></a>Paramètres

*indexArg*<br/>
Index de l'élément à définir.

*valueArg*<br/>
Valeur à définir à `indexArg`.

### <a name="return-value"></a>Valeur renvoyée

Référence à l'élément qui vient d'être défini.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la façon d’interpréter la valeur HRESULT, consultez [structure of com Error Codes](/windows/win32/com/structure-of-com-error-codes).

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](platform-namespace-c-cx.md)<br/>
[Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
