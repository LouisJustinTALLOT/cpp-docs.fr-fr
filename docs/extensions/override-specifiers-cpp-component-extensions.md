---
title: Spécificateurs de remplacement (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
ms.openlocfilehash: c1e8e7db2879b0226eaff562f5b5b826bce14caf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515744"
---
# <a name="override-specifiers--ccli-and-ccx"></a>Spécificateurs de remplacement (C++/CLI et C++/CX)

Les *spécificateurs de substitution* modifient le comportement des types hérités et des membres de types hérités dans les types dérivés.

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="remarks"></a>Remarques

Pour plus d'informations sur les spécificateurs de substitution, consultez :

- [abstract](abstract-cpp-component-extensions.md)

- [new (nouvel emplacement dans vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- [Spécificateurs de substitution et compilations natives](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

**abstract** et **sealed** sont également valides dans les déclarations de type, où ils ne se comportent pas comme des spécificateurs de substitution.

Pour plus d’informations sur la substitution explicite des fonctions de classe de base, consultez [Substitutions explicites](explicit-overrides-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows Runtime

(Aucune note de cette fonctionnalité de langage ne s’applique qu’au Windows Runtime.)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(Aucune note de cette fonctionnalité de langage ne s’applique qu’au Common Language Runtime.)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)