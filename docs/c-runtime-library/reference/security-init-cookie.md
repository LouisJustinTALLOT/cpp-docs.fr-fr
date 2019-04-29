---
title: __security_init_cookie
ms.date: 11/04/2016
apiname:
- __security_init_cookie
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- security_init_cookie
- __security_init_cookie
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
ms.openlocfilehash: c7b25e05b4574a7b397cd07d55000a5e53db58f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356834"
---
# <a name="securityinitcookie"></a>__security_init_cookie

Initialise le cookie de sécurité global.

## <a name="syntax"></a>Syntaxe

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>Notes

Le cookie de sécurité global est utilisé pour la protection contre le dépassement de mémoire tampon dans le code compilé avec [GS (Vérification de la sécurité de la mémoire tampon)](../../build/reference/gs-buffer-security-check.md), ainsi que dans le code qui utilise la gestion des exceptions. À l'entrée dans une fonction protégée contre le dépassement de mémoire tampon, le cookie est placé dans la pile. À la sortie, sa valeur dans la pile est comparée à celle du cookie global. Toute différence de valeur indique qu'un dépassement de mémoire tampon s'est produit, ce qui entraîne l'arrêt immédiat du programme.

Normalement, **__security_init_cookie** est appelée par la bibliothèque CRT quand il est initialisé. Si vous ignorez l’initialisation CRT, par exemple, si vous utilisez [/Entry](../../build/reference/entry-entry-point-symbol.md) pour spécifier un point d’entrée, vous devez l’appeler **__security_init_cookie** vous-même. Si **__security_init_cookie** n’est pas appelée, le cookie de sécurité est défini sur une valeur par défaut et la protection de dépassement de mémoire tampon est compromise. Comme un attaquant peut exploiter cette valeur de cookie par défaut pour tromper les contrôles de dépassement de mémoire tampon, nous vous recommandons de toujours appeler **__security_init_cookie** lorsque vous définissez votre propre point d’entrée.

L’appel à **__security_init_cookie** doit intervenir avant protégé de saturation de la fonction est entrée ; sinon un dépassement de mémoire tampon parasite est détecté. Pour plus d’informations, consultez [Erreur R6035 du Runtime C](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="example"></a>Exemple

Consultez les exemples présentés dans [Erreur R6035 du Runtime C](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h>|

**__security_init_cookie** est une extension Microsoft de la bibliothèque Runtime C standard. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Microsoft Security Response Center](https://www.microsoft.com/msrc?rtc=1)
