---
title: Support COM du compilateur | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b05fdff690f8693e926011c3bc7d1738ee9be66c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-com-support"></a>Prise en charge COM du compilateur
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Le compilateur Visual C++ peut directement lire les bibliothèques de types COM (Component Object Model) et traduire le contenu en code source C++ qui peut être inclus dans la compilation. Les extensions de langage sont disponibles pour simplifier la programmation COM côté client.  
  
 À l’aide de la [directive de préprocesseur #import](../preprocessor/hash-import-directive-cpp.md), le compilateur peut lire une bibliothèque de types et les convertir dans un fichier d’en-tête C++ qui décrit le modèle COM des interfaces en tant que classes. Un ensemble d'attributs `#import` est disponible pour permettre le contrôle utilisateur du contenu pour les fichiers d'en-tête de la bibliothèque de types obtenus.  
  
 Vous pouvez utiliser la [__declspec](../cpp/declspec.md) attribut étendu [uuid](../cpp/uuid-cpp.md) pour affecter un identificateur global unique (GUID) à un objet COM. Le mot clé [__uuidof](../cpp/uuidof-operator.md) peut être utilisé pour extraire le GUID associé à un objet COM. Un autre `__declspec` attribut, [propriété](../cpp/property-cpp.md), peut être utilisé pour spécifier le **obtenir** et **définir** méthodes pour un membre de données d’un objet COM.  
  
 Un ensemble de classes et fonctions globales de prise en charge COM est fourni pour prendre en charge la **VARIANT** et `BSTR` types implémentent des pointeurs intelligents et encapsuler l’objet d’erreur levé par `_com_raise_error`:  
  
-   [Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)  
  
-   [_bstr_t](../cpp/bstr-t-class.md)  
  
-   [_com_error](../cpp/com-error-class.md)  
  
-   [_com_ptr_t](../cpp/com-ptr-t-class.md)  
  
-   [_variant_t](../cpp/variant-t-class.md)  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Classes de prise en charge COM du compilateur](../cpp/compiler-com-support-classes.md)   
 [Fonctions globales COM du compilateur](../cpp/compiler-com-global-functions.md)