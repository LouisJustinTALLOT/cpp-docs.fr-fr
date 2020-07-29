---
title: Platform::STAThreadAttribute (classe)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
helpviewer_keywords:
- Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
ms.openlocfilehash: 6a8220d8cddca29e621b21fc56966efdb42cb32e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213019"
---
# <a name="platformstathreadattribute-class"></a>Platform::STAThreadAttribute (classe)

Indique que le modèle de thread d'une application est un modèle STA (Single-Threaded Apartment).

## <a name="syntax"></a>Syntaxe

```
public ref class STAThreadAttribute sealed : Attribute
```

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[STAThreadAttribute, constructeur 1](#ctor)|Initialise une nouvelle instance de la classe.|

### <a name="public-methods"></a>M&#233;thodes publiques

L’attribut STAThreadAttribute hérite de la [classe Platform :: Object](../cppcx/platform-object-class.md). STAThreadAttribute surcharge ou possède également les membres suivants :

|Nom|Description|
|----------|-----------------|
|[STAThreadAttribute::Equals](#equals)|Détermine si l'objet spécifié est égal à l'objet actuel.|
|[STAThreadAttribute::GetHashCode](#gethashcode)|Retourne le code de hachage de cette instance.|
|[STAThreadAttribute::ToString](#tostring)|Retourne une chaîne qui représente l'objet actif.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Platform`

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Platform

## <a name="stathreadattribute-constructor"></a><a name="ctor"></a> STAThreadAttribute constructor

Initialise une nouvelle instance de la classe STAThreadAttribute.

### <a name="syntax"></a>Syntaxe

```cpp
public:STAThreadAttribute();
```

## <a name="stathreadattributeequals"></a><a name="equals"></a>STAThreadAttribute :: Equals

Détermine si l'objet spécifié est égal à l'objet actuel.

### <a name="syntax"></a>Syntaxe

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>Paramètres

*obj*<br/>
Objet à comparer.

### <a name="return-value"></a>Valeur de retour

**`true`** Si les objets sont égaux ; Sinon, **`false`** .

## <a name="stathreadattributegethashcode"></a><a name="gethashcode"></a>STAThreadAttribute :: GetHashCode

Retourne le code de hachage de cette instance.

### <a name="syntax"></a>Syntaxe

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Valeur de retour

Code de hachage de cette instance.

## <a name="stathreadattributetostring"></a><a name="tostring"></a>STAThreadAttribute :: ToString

Retourne une chaîne qui représente l'objet actif.

### <a name="syntax"></a>Syntaxe

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Valeur de retour

Chaîne qui représente l’objet actif.

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](platform-namespace-c-cx.md)
