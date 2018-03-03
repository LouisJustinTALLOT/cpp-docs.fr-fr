---
title: nullptr | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- nullptr_cpp
dev_langs:
- C++
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3063a93361095a9d51152ce93f8522365513cf67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="nullptr"></a>nullptr
Désigne une constante de pointeur null du type `std::nullptr_t`, qui peut être convertie en tout type pointeur brut.  Bien que vous puissiez utiliser le mot clé `nullptr` sans inclure aucun en-tête, si votre code utilise le type `std::nullptr_t`, vous devez le définir en incluant l'en-tête `<cstddef>`.  
  
> [!NOTE]
>  Le mot clé `nullptr` est aussi défini dans C++/CLI pour les applications en code managé ; il n'est pas interchangeable avec le mot clé C++ de norme ISO. Si votre code peut être compilé à l’aide de la [/CLR](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur qui cible le code managé, puis utilisez `__nullptr` dans n’importe quelle ligne de code où vous devez vous assurer que le compilateur utilise l’interprétation C++ native. Pour plus d’informations, consultez [nullptr](../windows/nullptr-cpp-component-extensions.md).  
  
## <a name="remarks"></a>Notes  
 Évitez d'utiliser `NULL` ou zéro (`0`) comme constante de pointeur null ; `nullptr` est moins vulnérable aux risques d'utilisation incorrecte et fonctionne mieux dans la plupart des situations.  Par exemple, étant donné `func(std::pair<const char *, double>)`, l'appel à `func(std::make_pair(NULL, 3.14))` provoque une erreur du compilateur.  Étant donné que la macro NULL s'étend à `0`, l'appel `std::make_pair(0, 3.14)` retourne `std::pair<int, double>`, qui n'est pas convertible au type de paramètre `std::pair<const char *, double>` de func().  L'appel à `func(std::make_pair(nullptr, 3.14))` entraîne une compilation correcte, car `std::make_pair(nullptr, 3.14)` retourne `std::pair<std::nullptr_t, double>`, qui peut être convertie en `std::pair<const char *, double>`.  
  
## <a name="see-also"></a>Voir aussi  
 [Mots clés](../cpp/keywords-cpp.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)