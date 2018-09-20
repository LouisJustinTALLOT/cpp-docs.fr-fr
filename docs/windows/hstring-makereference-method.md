---
title: Hstring::makereference, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
dev_langs:
- C++
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ebc8632d273e650cf11e70177bbfbeb0e90e8601
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394853"
---
# <a name="hstringmakereference-method"></a>HString::MakeReference, méthode

Crée un `HStringReference` objet à partir d’un paramètre de chaîne spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>Paramètres

*sizeDest*<br/>
Un paramètre de modèle qui spécifie la taille de la destination `HStringReference` mémoire tampon.

*str*<br/>
Une référence à une chaîne à caractères larges.

*Len*<br/>
La longueur maximale de la *str* mémoire tampon de paramètre à utiliser dans cette opération. Si le *len* paramètre n’est pas spécifié, l’intégralité de *str* paramètre est utilisé.

## <a name="return-value"></a>Valeur de retour

Un `HStringReference` objet dont la valeur est identique à celui du texte spécifié *str* paramètre.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HString, classe](../windows/hstring-class.md)