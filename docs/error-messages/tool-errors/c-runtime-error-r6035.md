---
description: 'En savoir plus sur : erreur Runtime C R6035'
title: Erreur Runtime C R6035
ms.date: 11/04/2016
f1_keywords:
- R6035
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
ms.openlocfilehash: f316586bbfb5aa9d8b3fb1d30b5dea65bff19d26
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228389"
---
# <a name="c-runtime-error-r6035"></a>Erreur Runtime C R6035

Microsoft Visual C++ bibliothèque Runtime, erreur R6035-un module de cette application initialise le cookie de sécurité global du module lorsqu’une fonction qui s’appuie sur ce cookie de sécurité est active.  Appelez __security_init_cookie précédemment.

[__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md) doit être appelé avant la première utilisation du cookie de sécurité global.

Le cookie de sécurité global est utilisé pour la protection contre le dépassement de mémoire tampon dans le code compilé avec [/GS (vérification de la sécurité de la mémoire tampon)](../../build/reference/gs-buffer-security-check.md) et dans le code qui utilise la gestion structurée des exceptions. Essentiellement, à l’entrée dans une fonction protégée contre le dépassement de délai, le cookie est placé sur la pile et, à la sortie, la valeur sur la pile est comparée au cookie global. Toute différence entre elles indique qu’un dépassement de mémoire tampon s’est produit et entraîne l’arrêt immédiat du programme.

L’erreur R6035 indique qu’un appel à `__security_init_cookie` a été effectué après l’entrée d’une fonction protégée. Si l’exécution devait se poursuivre, un dépassement de mémoire tampon parasite est détecté, car le cookie sur la pile ne correspondrait plus au cookie global.

Prenons l’exemple de DLL suivant. Le point d’entrée de la DLL a la valeur DllEntryPoint via l’option de l’éditeur de liens [/entry (symbole du point d’entrée)](../../build/reference/entry-entry-point-symbol.md) . Cela contourne l’initialisation du CRT qui initialiserait normalement le cookie de sécurité global, de sorte que la DLL elle-même doit appeler `__security_init_cookie` .

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

Cet exemple génère l’erreur R6035, car DllEntryPoint utilise la gestion structurée des exceptions et utilise donc le cookie de sécurité pour détecter les dépassements de mémoire tampon. Lors de l’appel de DllInitialize, le cookie de sécurité global a déjà été placé sur la pile.

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

Dans ce cas, DllEntryPoint n’est pas protégé contre les dépassements de mémoire tampon (il n’a aucune mémoire tampon de chaîne locale et n’utilise pas la gestion structurée des exceptions); par conséquent, il peut appeler en toute sécurité `__security_init_cookie` . Il appelle ensuite une fonction d’assistance qui est protégée.

> [!NOTE]
> Le message d’erreur R6035 est généré uniquement par le CRT de débogage x86 et uniquement pour la gestion structurée des exceptions, mais la condition est une erreur sur toutes les plateformes, et pour toutes les formes de gestion des exceptions, telles que C++ EH.

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de sécurité dans MSVC](https://devblogs.microsoft.com/cppblog/security-features-in-microsoft-visual-c/)
