---
title: processus | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- process_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65ae8eef828a8abd4bf726c99850089c0f30b71b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032562"
---
# <a name="process"></a>process

Spécifie que votre processus d'application managé doit comporter une seule copie d'une variable globale particulière, d'une variable membre static ou d'une variable locale static partagée par tous les domaines d'application du processus. Cela a été principalement destinée à être utilisée lors de la compilation avec **/CLR : pure**, qui est déconseillé dans Visual Studio 2017 et non pris en charge dans Visual Studio 2017. Lors de la compilation avec **/CLR**, variables globales et static sont par le processus par défaut et n’avez pas besoin d’utiliser **__declspec (Process)**.

Seules une variable globale, une variable membre static ou une variable locale statique de type natif peut être marquée avec **__declspec (Process)**.

**processus** est valide uniquement lors de la compilation avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

Si vous souhaitez que chaque domaine d’application possède sa propre copie d’une variable globale, utiliser [appdomain](../cpp/appdomain.md).

Consultez [domaines d’Application et Visual C++](../dotnet/application-domains-and-visual-cpp.md) pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
