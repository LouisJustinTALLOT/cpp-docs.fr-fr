---
title: Transfert de type (C + c++ / CLI) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type forwarding, Visual C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6898c011a4e2e907cd745ccb206b0e0f0b37e78f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="type-forwarding-ccli"></a>Transfert de type (C++/CLI)
*Transfert de type* vous permet de déplacer un type d’un assembly (assembly A) dans un autre assembly (assembly B), tel qu’il n’est pas nécessaire de recompiler les clients qui utilisent l’assembly A.  
  
## <a name="all-platforms"></a>Toutes les plateformes  
 Cette fonctionnalité n’est pas pris en charge dans tous les runtimes.  
  
## <a name="windows-runtime"></a>Windows Runtime  
 Cette fonctionnalité n’est pas pris en charge dans le Windows Runtime.  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 L’exemple de code suivant montre comment utiliser le transfert de type.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
#using "new.dll"  
[assembly:TypeForwardedTo(type::typeid)];  
```  
  
### <a name="parameters"></a>Paramètres  
 `new`  
 L’assembly dans lequel vous déplacez la définition de type.  
  
 `type`  
 Le type dont la définition vous déplacez dans un autre assembly.  
  
### <a name="remarks"></a>Notes  
 Une fois un composant (assembly) est fourni et est utilisé par les applications clientes, vous pouvez utiliser pour déplacer un type à partir du composant (assembly) dans un autre assembly, expédier le composant mis à jour (et tous les assemblys supplémentaires requises) de transfert de type et le client applications continueront de fonctionner sans être recompilé.  
  
 Transfert de type fonctionne uniquement pour les composants référencés par les applications existantes. Lorsque vous régénérez une application, il faut les références d’assembly approprié pour tous les types utilisés dans l’application.  
  
 Lors du transfert d’un type (Type A) à partir d’un assembly, vous devez ajouter le `TypeForwardedTo` attribut pour ce type, ainsi que d’une référence d’assembly. L’assembly que vous référencez doit contenir une des opérations suivantes :  
  
-   La définition de Type a.  
  
-   A `TypeForwardedTo` attribut de Type A, ainsi que d’une référence d’assembly.  
  
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
  
 Par conséquent, si un fichier de code source qui est utilisé pour générer l’assembly.dll contient une définition de type (`ref class MyClass`), et que vous souhaitez déplacer ce type de définition de l’assembly B.dll, vous devez :  
  
1.  Déplacer le `MyClass` définition dans un fichier de code source utilisé pour générer B.dll de type.  
  
2.  Générer l’assembly B.dll  
  
3.  Supprimer le `MyClass` , type de définition à partir du code source utilisé pour générer des.dll et remplacez-le par le code suivant :  
  
    ```  
    #using "B.dll"  
    [assembly:TypeForwardedTo(MyClass::typeid)];  
    ```  
  
4.  Générer un assembly.dll.  
  
5.  Utilisez.dll sans avoir à recompiler les applications clientes.  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**