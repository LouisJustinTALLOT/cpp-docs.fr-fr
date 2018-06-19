---
title: C Runtime erreur R6035 | Documents Microsoft
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
ms.openlocfilehash: ecadf1793475e1cf5f354796c71a1894884e24e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299745"
---
# <a name="c-runtime-error-r6035"></a>R6035 d’erreur d’exécution C
Bibliothèque Microsoft Visual C++ Runtime, erreur R6035 - un module de cette application initialisation du cookie de sécurité global du module alors qu’une fonction utilisant ce cookie de sécurité est active.  Appelez __security_init_cookie précédemment.  
  
 [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md) doit être appelée avant la première utilisation du cookie de sécurité global.  
  
 Le cookie de sécurité global est utilisé pour la protection de dépassement de mémoire tampon dans le code compilé avec [/GS (vérification de la sécurité de la mémoire tampon)](../../build/reference/gs-buffer-security-check.md) et dans le code qui utilise la gestion structurée des exceptions. Essentiellement, à l’entrée à une fonction protégée, le cookie est placé sur la pile, et à la sortie, la valeur sur la pile est comparée à celle du cookie global. Toute différence indique qu’un dépassement de mémoire tampon s’est produite et entraîne l’arrêt immédiat du programme.  
  
 Erreur R6035 indique qu’un appel à `__security_init_cookie` a été effectuée après l’entrée dans une fonction protégée. Si l’exécution devait se poursuivre, un dépassement de mémoire tampon parasite serait détecté car le cookie de la pile ne correspondrait plus au cookie global.  
  
 Prenons l’exemple suivant de la DLL. Le point d’entrée DLL a la valeur DllEntryPoint via l’éditeur de liens [/ENTRY (symbole de Point d’entrée)](../../build/reference/entry-entry-point-symbol.md) option. Ceci permet d’ignorer l’initialisation du CRT qui initialise normalement le cookie de sécurité global, afin que la DLL proprement dite doit appeler `__security_init_cookie`.  
  
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
  
 Cet exemple génère l’erreur R6035 car DllEntryPoint utilise la gestion structurée des exceptions et donc, le cookie de sécurité pour détecter les saturations de mémoire tampon. À la fois que lorsque DllInitialize est appelé, le cookie de sécurité global a déjà été placé sur la pile.  
  
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
  
 Dans ce cas, DllEntryPoint n’est pas protégé contre les dépassements de mémoire tampon (il contient aucune mémoire tampon de chaîne locale et n’utilise pas de gestion structurée des exceptions) ; Par conséquent, il peut appeler en toute sécurité `__security_init_cookie`. Il appelle ensuite une fonction d’assistance qui est protégée.  
  
> [!NOTE]
>  Message d’erreur R6035 est uniquement généré par le x86 de débogage CRT, et uniquement pour la gestion structurée des exceptions, mais la condition est une erreur sur toutes les plateformes et pour toutes les formes de l’exception gestion, tels que C++ EH.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles approfondis de la sécurité du compilateur](http://go.microsoft.com/fwlink/p/?linkid=7260)