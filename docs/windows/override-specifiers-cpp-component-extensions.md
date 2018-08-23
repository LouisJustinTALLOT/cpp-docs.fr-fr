---
title: Spécificateurs de substitution (Extensions du composant C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- override specifiers, Visual C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 71cafe3d73204b6a318e731d0a95f2dfcc73fa5a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600121"
---
# <a name="override-specifiers--c-component-extensions"></a>Spécificateurs de substitution (extensions du composant C++)

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

[Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)