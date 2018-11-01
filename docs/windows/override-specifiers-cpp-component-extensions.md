---
title: Spécificateurs de substitution (C++ / c++ / CLI et c++ / CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
ms.openlocfilehash: 9d839b9530cff144cda7897b0c96af48c14454a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639853"
---
# <a name="override-specifiers--ccli-and-ccx"></a>Spécificateurs de substitution (C++ / c++ / CLI et c++ / CX)

*Spécificateurs de substitution* modifier le comportement des types hérités et les membres de types hérités se comportent dans les types dérivés.

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="remarks"></a>Notes

Pour plus d'informations sur les spécificateurs de substitution, consultez :

- [abstract](../windows/abstract-cpp-component-extensions.md)

- [New (nouvel emplacement dans vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](../windows/override-cpp-component-extensions.md)

- [sealed](../windows/sealed-cpp-component-extensions.md)

- [Spécificateurs de substitution et Compilations natives](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

**abstraite** et **sealed** sont également valides dans les déclarations de type, où qu’ils n’agissent pas comme spécificateurs de substitution.

Pour plus d’informations sur la substitution explicite des fonctions de classe de base, consultez [substitutions explicites](../windows/explicit-overrides-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows Runtime

(Aucune note de cette fonctionnalité de langage ne s’applique qu’au Windows Runtime.)

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(Aucune note de cette fonctionnalité de langage ne s'applique qu'au Common Language Runtime.)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](../windows/component-extensions-for-runtime-platforms.md)