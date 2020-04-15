---
title: Erreur Runtime C R6035
ms.date: 11/04/2016
f1_keywords:
- R6035
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
ms.openlocfilehash: ff3cd0259df92aa5cdade3f78a240e69f8f6f7de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377477"
---
# <a name="c-runtime-error-r6035"></a>Erreur Runtime C R6035

Microsoft Visual CMD Runtime Library, Error R6035 - Un module de cette application est l’initialisation du cookie de sécurité global du module alors qu’une fonction reposant sur ce cookie de sécurité est active.  Appelez __security_init_cookie plus tôt.

[__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md) doit être appelé avant la première utilisation du cookie de sécurité global.

Le cookie de sécurité global est utilisé pour la protection des dépassements de mémoire tampon dans le code compilé avec [/GS (Buffer Security Check)](../../build/reference/gs-buffer-security-check.md) et dans le code qui utilise la manipulation structurée des exceptions. Essentiellement, à l’entrée d’une fonction protégée par dépassement, le cookie est mis sur la pile, et à la sortie, la valeur sur la pile est comparée au cookie global. Toute différence entre eux indique qu’un dépassement de tampon s’est produit et entraîne la résiliation immédiate du programme.

L’erreur R6035 indique `__security_init_cookie` qu’un appel a été fait après qu’une fonction protégée a été saisie. Si l’exécution devait se poursuivre, un faux dépassement de mémoire tampon serait détecté parce que le cookie sur la pile ne correspondrait plus au cookie global.

Prenons l’exemple suivant de DLL. Le point d’entrée DLL est réglé sur DllEntryPoint via l’option [linker/ENTRY (Entry-Point Symbol).](../../build/reference/entry-entry-point-symbol.md) Cela contourne l’initialisation de la CRT qui serait ordinairement initialiser le cookie `__security_init_cookie`de sécurité mondiale, de sorte que le DLL lui-même doit appeler .

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

Cet exemple générera l’erreur R6035 parce que DllEntryPoint utilise la manipulation d’exception structurée et utilise donc le cookie de sécurité pour détecter les dépassements de mémoire tampon. Au moment où DllInitialize est appelé, le cookie de sécurité mondiale a déjà été mis sur la pile.

La bonne façon est démontrée dans cet exemple :

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

Dans ce cas, DllEntryPoint n’est pas protégé contre les dépassements de mémoire tampon (il n’a pas de tampons à cordes locales et n’utilise pas de manipulation d’exception structurée); par conséquent, il `__security_init_cookie`peut appeler en toute sécurité . Il appelle ensuite une fonction d’aide qui est protégée.

> [!NOTE]
> Le message d’erreur R6035 n’est généré que par le CRT de débogé x86, et uniquement pour la manipulation structurée des exceptions, mais la condition est une erreur sur toutes les plates-formes, et pour toutes les formes de manipulation d’exception, telles que L.ID.

## <a name="see-also"></a>Voir aussi

[Caractéristiques de sécurité dans MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)
