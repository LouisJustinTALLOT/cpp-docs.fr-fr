---
description: 'En savoir plus sur : classe Platform :: MTAThreadAttribute'
title: Platform::MTAThreadAttribute (classe)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
ms.openlocfilehash: cc8586b37b4e5a1f6a6d0f33a27a21acca4aceb0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308365"
---
# <a name="platformmtathreadattribute-class"></a>Platform::MTAThreadAttribute (classe)

Indique que le modèle de thread d'une application est un modèle MTA (MultiThreaded Apartment).

## <a name="syntax"></a>Syntaxe

```
public ref class MTAThreadAttribute sealed : Attribute
```

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[MTAThreadAttribute, constructeur 1](#ctor) , constructeur|Initialise une nouvelle instance de la classe.|

### <a name="public-methods"></a>M&#233;thodes publiques

L’attribut MTAThreadAttribute hérite de la [classe Platform :: Object](../cppcx/platform-object-class.md). MTAThreadAttribute surcharge ou possède également les membres suivants :

|Nom|Description|
|----------|-----------------|
|[MTAThreadAttribute::Equals](#equals)|Détermine si l'objet spécifié est égal à l'objet actuel.|
|[MTAThreadAttribute::GetHashCode](#gethashcode)|Retourne le code de hachage de cette instance.|
|[MTAThreadAttribute::ToString](#tostring)|Retourne une chaîne qui représente l'objet actuel.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Platform`

### <a name="requirements"></a>Spécifications

**Métadonnées :** Platform. winmd

**Espace de noms :** Platform

## <a name="mtathreadattribute-constructor"></a><a name="ctor"></a> MTAThreadAttribute, constructeur

Initialise une nouvelle instance de la classe MTAThreadAttribute.

### <a name="syntax"></a>Syntaxe

```cpp
public:MTAThreadAttribute();
```

## <a name="mtathreadattributeequals"></a><a name="equals"></a> MTAThreadAttribute :: Equals

Détermine si l'objet spécifié est égal à l'objet actuel.

### <a name="syntax"></a>Syntaxe

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>Paramètres

*obj*<br/>
Objet à comparer.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les objets sont égaux ; Sinon, **`false`** .

## <a name="mtathreadattributegethashcode"></a><a name="gethashcode"></a> MTAThreadAttribute :: GetHashCode

Retourne le code de hachage de cette instance.

### <a name="syntax"></a>Syntaxe

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Valeur de retour

Code de hachage de cette instance.

## <a name="mtathreadattributetostring"></a><a name="tostring"></a> MTAThreadAttribute :: ToString

Retourne une chaîne qui représente l'objet actuel.

### <a name="syntax"></a>Syntaxe

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Valeur de retour

Chaîne qui représente l'objet actuel.

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](platform-namespace-c-cx.md)
