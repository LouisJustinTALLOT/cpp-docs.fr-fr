---
title: Pimpl pour l’Encapsulation au moment de la compilation (Modern C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f611a898018cee5edc031be1db2fd35af8857e16
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420153"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Pimpl pour l’encapsulation au moment de la compilation (Modern C++)
Le *pimpl idiome* est une technique C++ moderne pour masquer l’implémentation, afin de minimiser le couplage, and pour séparer les interfaces. Pimpl est l’abréviation de « pointeur vers l’implémentation. » Vous pouvez déjà être familiarisé avec le concept, mais il connaître d’autres noms comme l’idiome malicieusement ou du compilateur pare-feu.  
  
## <a name="why-use-pimpl"></a>Pourquoi utiliser pimpl ?  
 Voici comment l’idiome pimpl peut améliorer le cycle de vie de développement logiciel :  
  
-   Minimisation des dépendances de compilation.  
  
-   Séparation de l’interface et l’implémentation.  
  
-   Portabilité.  
  
## <a name="pimpl-header"></a>Pimpl en-tête  
  
```cpp  
// my_class.h  
class my_class {  
   //  ... all public and protected stuff goes here ...  
private:  
   class impl; unique_ptr<impl> pimpl; // opaque type here  
};  
  
```  
  
 L’idiome pimpl évite les cascades de reconstruction et de mises en page de l’objet fragile. Il est particulièrement adaptée pour les types courants (de manière transitive).  
  
## <a name="pimpl-implementation"></a>Implémentation de Pimpl  
 Définir la `impl` classe dans le fichier .cpp.  
  
```cpp  
// my_class.cpp  
class my_class::impl {  // defined privately here  
  // ... all private data and functions: all of these  
  //     can now change without recompiling callers ...  
};  
my_class::my_class(): pimpl( new impl )  
{  
  // ... set impl values ...   
}  
```  
  
## <a name="best-practices"></a>Recommandations  
 Pensez à ajouter la prise en charge pour la spécialisation de permutation non lanceurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Référence du langage C++](../cpp/cpp-language-reference.md)   
 [Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)