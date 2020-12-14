---
description: 'En savoir plus sur : `process`'
title: processus
ms.date: 11/04/2016
f1_keywords:
- process_cpp
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
ms.openlocfilehash: ea5baee65b3375e062939f49bc30f3780c312852
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198594"
---
# `process`

Spécifie que votre processus d'application managé doit comporter une seule copie d'une variable globale particulière, d'une variable membre static ou d'une variable locale static partagée par tous les domaines d'application du processus. Cela était principalement destiné à être utilisé lors de la compilation avec **`/clr:pure`** , qui est déconseillé dans Visual studio 2015 et non pris en charge dans Visual studio 2017. Lors de la compilation avec **`/clr`** , les variables globales et statiques sont par processus par défaut et n’ont pas besoin d’utiliser **`__declspec(process)`** .

Seule une variable globale, une variable membre statique ou une variable locale statique de type natif peut être marquée avec **`__declspec(process)`** .

**`process`** est valide uniquement lors de la compilation avec [`/clr`](../build/reference/clr-common-language-runtime-compilation.md) .

Si vous souhaitez que chaque domaine d’application dispose de sa propre copie d’une variable globale, utilisez [AppDomain](../cpp/appdomain.md).

Pour plus d’informations [, consultez domaines d’application et Visual C++](../dotnet/application-domains-and-visual-cpp.md) .

## <a name="see-also"></a>Voir aussi

[`__declspec`](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
