---
description: 'En savoir plus sur : __security_init_cookie'
title: __security_init_cookie
ms.date: 11/04/2016
api_name:
- __security_init_cookie
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- security_init_cookie
- __security_init_cookie
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
ms.openlocfilehash: 48051eb34e7fe9fe1e32e41849072f71d6665d94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288943"
---
# <a name="__security_init_cookie"></a>__security_init_cookie

Initialise le cookie de sécurité global.

## <a name="syntax"></a>Syntaxe

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>Notes

Le cookie de sécurité global est utilisé pour la protection contre le dépassement de mémoire tampon dans le code compilé avec [GS (Vérification de la sécurité de la mémoire tampon)](../../build/reference/gs-buffer-security-check.md), ainsi que dans le code qui utilise la gestion des exceptions. À l'entrée dans une fonction protégée contre le dépassement de mémoire tampon, le cookie est placé dans la pile. À la sortie, sa valeur dans la pile est comparée à celle du cookie global. Toute différence de valeur indique qu'un dépassement de mémoire tampon s'est produit, ce qui entraîne l'arrêt immédiat du programme.

Normalement, **__security_init_cookie** est appelé par le CRT lorsqu’il est initialisé. Si vous ignorez l’initialisation CRT (par exemple, si vous utilisez [/entry](../../build/reference/entry-entry-point-symbol.md) pour spécifier un point d’entrée), vous devez appeler **__security_init_cookie** vous-même. Si **__security_init_cookie** n’est pas appelé, le cookie de sécurité global est défini sur une valeur par défaut et la protection contre le dépassement de mémoire tampon est compromise. Comme une personne malveillante peut exploiter cette valeur de cookie par défaut pour contrecarrer les contrôles de dépassement de mémoire tampon, nous vous recommandons de toujours appeler **__security_init_cookie** lorsque vous définissez votre propre point d’entrée.

L’appel à **__security_init_cookie** doit être effectué avant l’entrée d’une fonction protégée contre le dépassement de délai. dans le cas contraire, un dépassement de mémoire tampon parasite est détecté. Pour plus d’informations, consultez [Erreur R6035 du Runtime C](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="example"></a>Exemple

Consultez les exemples présentés dans [Erreur R6035 du Runtime C](../../error-messages/tool-errors/c-runtime-error-r6035.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h>|

**__security_init_cookie** est une extension Microsoft de la bibliothèque Runtime C standard. Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Centre de réponse aux problèmes de sécurité Microsoft](https://www.microsoft.com/msrc?rtc=1)
