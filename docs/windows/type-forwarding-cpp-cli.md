---
title: Transfert de type (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- type forwarding, Visual C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 627b0a881795a963e3739accc351ee684b7b8232
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644932"
---
# <a name="type-forwarding-ccli"></a>Transfert de type (C++/CLI)
*Transfert de type* vous permet de déplacer un type à partir d’un assembly (assembly A) dans un autre assembly (assembly B), tel qu’il n’est pas nécessaire de recompiler les clients qui utilisent l’assembly A.  
  
## <a name="all-platforms"></a>Toutes les plateformes  
 Cette fonctionnalité n’est pas pris en charge dans tous les runtimes.  
  
## <a name="windows-runtime"></a>Windows Runtime  
 Cette fonctionnalité n’est pas pris en charge dans le Runtime de Windows.  
  
### <a name="requirements"></a>Configuration requise  
 Option du compilateur : `/ZW`  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 L’exemple de code suivant montre comment utiliser le transfert de type.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
#using "new.dll"  
[assembly:TypeForwardedTo(type::typeid)];  
```  
  
### <a name="parameters"></a>Paramètres  
 *new*  
 L’assembly dans lequel vous déplacez la définition de type.  
  
 *type*  
 Le type dont la définition vous déplacez dans un autre assembly.  
  
### <a name="remarks"></a>Notes  
 Une fois un composant (assembly) est fourni et est utilisé par les applications clientes, vous pouvez utiliser transfert pour déplacer un type à partir du composant (assembly) dans un autre assembly, d’expédier le composant mis à jour (et autres assemblys requis) de type et le client applications continue de fonctionner sans être recompilé.  
  
 Le transfert de type fonctionne uniquement pour les composants référencés par les applications existantes. Lors de la reconstruction d’une application, il doit y avoir des références d’assembly appropriées pour tous les types utilisés dans l’application.  
  
 Lorsque le transfert de type (Type A) à partir d’un assembly, vous devez ajouter le `TypeForwardedTo` attribut pour ce type, ainsi que d’une référence d’assembly. L’assembly que vous référencez doit contenir une des opérations suivantes :  
  
-   La définition de Type a.  
  
-   Un `TypeForwardedTo` attribut de Type A, ainsi que d’une référence d’assembly.  
  
 Voici quelques exemples de types qui peuvent être transférés :  
  
-   classes ref  
  
-   classes de valeur  
  
-   enums  
  
-   interfaces  
  
 Vous ne pouvez pas transférer les types suivants :  
  
-   Types génériques  
  
-   Types natifs  
  
-   Les types imbriqués (si vous souhaitez transférer un type imbriqué, vous devez transférer le type englobant)  
  
 Vous pouvez transférer un type à un assembly créé dans n’importe quel langage ciblant le common language runtime.  
  
 Par conséquent, si un fichier de code source qui est utilisé pour générer l’assembly A.dll contient une définition de type (`ref class MyClass`), et que vous voulez déplacer ce type de définition de l’assembly B.dll, vous le feriez pour :  
  
1.  Déplacer le `MyClass` définition dans un fichier de code source utilisé pour générer B.dll de type.  
  
2.  Générer l’assembly B.dll  
  
3.  Supprimer le `MyClass` , type de définition à partir du code source utilisé pour générer A.dll et remplacez-le par le code suivant :  
  
    ```  
    #using "B.dll"  
    [assembly:TypeForwardedTo(MyClass::typeid)];  
    ```  
  
4.  Générer l’assembly.dll.  
  
5.  Utilisez A.dll sans avoir à recompiler les applications clientes.  
  
### <a name="requirements"></a>Configuration requise  
 Option du compilateur : `/clr`