---
title: Erreur Runtime C R6035 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6035
dev_langs:
- C++
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa300619d59bdcf4295c8db9f8e9ebf1acb6bb3a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683588"
---
# <a name="c-runtime-error-r6035"></a>Erreur Runtime C R6035
Bibliothèque Microsoft Visual C++ Runtime, erreur R6035 - un module de cette application initialisation du cookie de sécurité global du module alors qu’une fonction s’appuyer sur ce cookie de sécurité est active.  Appelez __security_init_cookie précédemment.  
  
 [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md) doit être appelée avant la première utilisation du cookie de sécurité global.  
  
 Le cookie de sécurité global est utilisé pour la protection de dépassement de mémoire tampon dans le code compilé avec [/GS (vérification de la sécurité de la mémoire tampon)](../../build/reference/gs-buffer-security-check.md) et dans le code qui utilise la gestion structurée des exceptions. Pour l’essentiel, à l’entrée à une fonction protégée de saturation, le cookie est placé sur la pile, et à la sortie, la valeur sur la pile est comparée à celle du cookie global. Une différence entre eux indique qu’un dépassement de mémoire tampon s’est produite et entraîne l’arrêt immédiat du programme.  
  
 Erreur R6035 indique qu’un appel à `__security_init_cookie` a été effectuée après l’entrée dans une fonction protégée. Si l’exécution doit continuer, un dépassement de mémoire tampon parasite serait détecté car le cookie de la pile ne correspondrait plus au cookie global.  
  
 Prenons l’exemple suivant de la DLL. Le point d’entrée DLL est la valeur DllEntryPoint via l’éditeur de liens [/ENTRY (symbole de Point d’entrée)](../../build/reference/entry-entry-point-symbol.md) option. Cela contourne l’initialisation du CRT qui initialise normalement le cookie de sécurité global, la DLL proprement dite doit donc appeler `__security_init_cookie`.  
  
```  
// Wrong way to call __security_init_cookie  
DllEntryPoint(...) {  
   DllInitialize();  
   ...  
   __try {  
      ...  
   } __except()... {  
      ...  
   }  
}  
  
void DllInitialize() {  
   __security_init_cookie();  
}  
```  
  
 Cet exemple génère l’erreur R6035 car DllEntryPoint utilise la gestion structurée des exceptions et donc, le cookie de sécurité pour détecter les dépassements de mémoire tampon. Au terme du délai que lorsque DllInitialize est appelé, le cookie de sécurité global a déjà été mis sur la pile.  
  
 La méthode correcte est illustrée dans cet exemple :  
  
```  
// Correct way to call __security_init_cookie  
DllEntryPoint(...) {  
   __security_init_cookie();  
   DllEntryHelper();  
}  
  
void DllEntryHelper() {  
   ...  
   __try {  
      ...  
   } __except()... {  
      ...  
   }  
}  
```  
  
 Dans ce cas, DllEntryPoint n’est pas protégé contre les dépassements de mémoire tampon (il n’a aucune mémoire tampon de chaîne locale et n’utilise pas structurée des exceptions) ; Par conséquent, elle peut appeler en toute sécurité `__security_init_cookie`. Il appelle ensuite une fonction d’assistance qui est protégée.  
  
> [!NOTE]
>  Message d’erreur R6035 est uniquement généré par le x86 de débogage CRT, et uniquement pour la gestion structurée des exceptions, mais la condition est une erreur sur toutes les plateformes et pour toutes les formes de l’exception gestion, tels que C++ EH.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de sécurité dans MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)