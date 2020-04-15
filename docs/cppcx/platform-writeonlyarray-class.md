---
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
ms.openlocfilehash: d06ed19b7c041f9ae73f862ba521449a206aa321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374647"
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray (classe)

Représente un tableau unidimensionnel utilisé comme paramètre d'entrée lorsque l'appelant transmet un tableau à remplir pour la méthode.

Cette classe ref est déclarée comme privée dans vccorlib.h. Par conséquent, elle n'est pas émise dans les métadonnées et est uniquement consommable à partir de C++. Cette classe est prévue uniquement pour être utilisée comme paramètre d'entrée qui accepte un tableau que l'appelant a alloué. Elle n'est pas constructible à partir du code utilisateur. Il permet à la méthode C++ d'écrire directement dans ce tableau, un modèle appelé modèle *FillArray* . Pour plus d’informations, voir [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="syntax"></a>Syntaxe

```cpp
private ref class WriteOnlyArray<T, 1>
```

### <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

Ces méthodes offrent une accessibilité interne, c'est-à-dire qu'elles ne sont accessibles que dans l'application ou le composant C++.

|Nom|Description|
|----------|-----------------|
|[WriteOnlyArray::commencer](#begin)|Itérateur qui pointe vers le premier élément du tableau.|
|[WriteOnlyArray::Data](#data)|Pointeur vers le tampon de données.|
|[WriteOnlyArray::fin](#end)|Itérateur qui pointe vers un élément au-delà du dernier élément du tableau.|
|[WriteOnlyArray::FastPass](#fastpass)|Indique si le tableau peut utiliser le mécanisme FastPass, qui est une optimisation exécutée en toute transparence par le système. N'utilisez pas cela dans votre code|
|[WriteOnlyArray::Longueur](#length)|Retourne le nombre d'éléments du tableau.|
|[WriteOnlyArray::set](#set)|Définit l'élément spécifié sur la valeur spécifiée.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`WriteOnlyArray`

### <a name="requirements"></a>Spécifications

Option du compilateur : **/ZW**

**Métadonnées :** platform.winmd

**Espace de noms :** Platform

## <a name="writeonlyarraybegin-method"></a><a name="begin"></a>WriteOnlyArray::commencer la méthode

Retourne un pointeur désignant le premier élément du tableau.

### <a name="syntax"></a>Syntaxe

```cpp
T* begin() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur désignant le premier élément du tableau.

### <a name="remarks"></a>Notes

Cet itérateur peut être utilisé avec les algorithmes STL tels que `std::sort` pour exécuter des opérations sur les élément du tableau.

## <a name="writeonlyarraydata-property"></a><a name="data"></a>WriteOnlyArray::Data Propriété

Pointeur vers le tampon de données.

### <a name="syntax"></a>Syntaxe

```cpp
property T* Data{
   T* get() const;
}
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers les octets bruts de tableau.

## <a name="writeonlyarrayend-method"></a><a name="end"></a>WriteOnlyArray::Méthode de fin

Retourne un pointeur sur un point suivant au-delà du dernier élément du tableau.

### <a name="syntax"></a>Syntaxe

```cpp
T* end() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur de pointeur sur un point suivant au-delà du dernier élément du tableau.

### <a name="remarks"></a>Notes

Cet itérateur peut être utilisé avec les algorithmes STL pour exécuter des opérations telles que `std::sort` sur les éléments de tableau.

## <a name="writeonlyarrayfastpass-property"></a><a name="fastpass"></a>WriteOnlyArray:FastPass Propriété

Indique si l'optimisation interne FastPass peut être exécutée. Non destiné à être utilisé par le code utilisateur.

### <a name="syntax"></a>Syntaxe

```cpp
property bool FastPass{
   bool get() const;
}
```

### <a name="return-value"></a>Valeur de retour

Valeur booléenne qui indique si le tableau est FastPass.

## <a name="writeonlyarrayget-method"></a><a name="get"></a>WriteOnlyArray:get Method

Retourne l'élément à l'index spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
T& get(unsigned int indexArg) const;
```

### <a name="parameters"></a>Paramètres

*indexArg*<br/>
L’index à utiliser.

### <a name="return-value"></a>Valeur de retour

## <a name="writeonlyarraylength-property"></a><a name="length"></a>WriteOnlyArray::Propriété De longueur

Retourne le nombre d'éléments du tableau alloué par l'appelant.

### <a name="syntax"></a>Syntaxe

```cpp
property unsigned int Length{
   unsigned int get() const;
}
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans le tableau.

## <a name="writeonlyarrayset-function"></a><a name="set"></a>WriteOnlyArray::set Function

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

*valeurArg*<br/>
Valeur à définir à `indexArg`.

### <a name="return-value"></a>Valeur de retour

Référence à l'élément qui vient d'être défini.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la façon d’interpréter la valeur HRESULT, voir [Structure of COM Error Codes](/windows/win32/com/structure-of-com-error-codes).

## <a name="see-also"></a>Voir aussi

[Espace nom de la plate-forme](platform-namespace-c-cx.md)<br/>
[Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
