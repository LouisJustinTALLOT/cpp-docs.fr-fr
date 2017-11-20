---
title: Attributs (C + c++ / CX) | Documents Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 4cffb903bcfa22654d4b8ff65609342fab267412
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="attributes-ccx"></a>Attributs (C++/CX)
Un attribut est un type spécial de classe ref qui peut être ajouté entre crochets aux types Windows Runtime et des méthodes pour spécifier certains comportements de la création de métadonnées. Plusieurs attributs prédéfinis, par exemple, [Windows::Foundation::Metadata::WebHostHidden](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx), sont couramment utilisés dans C + c++ / code CX. Cet exemple montre comment l'attribut est appliqué à une classe :  
  
 [!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]  
  
## <a name="custom-attributes"></a>Attributs personnalisés  
 Vous pouvez également définir des attributs personnalisés. Attributs personnalisés doivent être conformes à ces règles de Windows Runtime :  
  
-   Les attributs personnalisés ne peuvent contenir que des champs publics.  
  
-   Les champs d'attributs personnalisés peuvent être initialisés lorsque l'attribut est appliqué à une classe.  
  
-   Un champ peut être l'un de ces types :  
  
    -   int32 (entier)  
  
    -   uint32 (entier non signé)  
  
    -   bool  
  
    -   Platform::String^  
  
    -   Windows::Foundation::HResult  
  
    -   Platform::Type^  
  
    -   classe Enum publique (inclut des énumérations définies par l'utilisateur)  
  
 L'exemple suivant indique comment définir un attribut personnalisé et l'initialiser pour l'utiliser.  
  
 [!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]  
  
## <a name="see-also"></a>Voir aussi  
 [Système de type (C++/CX)](../cppcx/type-system-c-cx.md)   
 [Référence du langage Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)