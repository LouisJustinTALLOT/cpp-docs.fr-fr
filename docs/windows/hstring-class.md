---
title: HString, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
dev_langs:
- C++
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eea40f989e7d41afbff2773fcc5e6e5b2cfbafd2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613651"
---
# <a name="hstring-class"></a>HString, classe

Une classe d’assistance pour la gestion de la durée de vie d’une chaîne HSTRING utilisant le modèle RAII.

## <a name="syntax"></a>Syntaxe

```cpp
class HString;
```

## <a name="remarks"></a>Notes

Le Runtime Windows fournit l’accès aux chaînes via les handles HSTRING. Le **HString** classe fournit des fonctions de commodité et d’opérateurs pour simplifier l’utilisation des handles HSTRING. Cette classe peut gérer la durée de vie de la fonction HSTRING qu’il détient via un modèle RAII.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[HString::HString, constructeur](../windows/hstring-hstring-constructor.md)|Initialise une nouvelle instance de la **HString** classe.|
|[HString::~HString, destructeur](../windows/hstring-tilde-hstring-destructor.md)|Détruit l’instance actuelle de la **HString** classe.|

### <a name="members"></a>Membres

|Nom|Description|
|----------|-----------------|
|[HString::Set, méthode](../windows/hstring-set-method.md)|Définit la valeur de cours **HString** objet à la chaîne de caractères larges spécifiée ou **HString** paramètre.|
|[HString::Attach, méthode](../windows/hstring-attach-method.md)|Associe les **HString** objet actuelle **HString** objet.|
|[HString::CopyTo, méthode](../windows/hstring-copyto-method.md)|Copie en cours **HString** objet dans un objet HSTRING.|
|[HString::Detach, méthode](../windows/hstring-detach-method.md)|Dissocie spécifié **HString** objet à partir de sa valeur sous-jacente.|
|[HString::GetAddressOf, méthode](../windows/hstring-getaddressof-method.md)|Récupère un pointeur vers le handle HSTRING sous-jacent.|
|[HString::Get, méthode](../windows/hstring-get-method.md)|Récupère la valeur du handle HSTRING sous-jacent.|
|[HString::Release, méthode](../windows/hstring-release-method.md)|Supprime la valeur de chaîne sous-jacente et initialise actuel **HString** objet à une valeur vide.|
|[HString::MakeReference, méthode](../windows/hstring-makereference-method.md)|Crée un `HStringReference` objet à partir d’un paramètre de chaîne spécifiée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[HString::Operator=, opérateur](../windows/hstring-operator-assign-operator.md)|Déplace la valeur d’un autre **HString** objet actuel **HString** objet.|
|[HString::Operator==, opérateur](../windows/hstring-operator-equality-operator.md)|Indique si les deux paramètres sont égaux.|
|[HString::Operator!=, opérateur](../windows/hstring-operator-inequality-operator.md)|Indique si les deux paramètres ne sont pas égales.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HString`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)