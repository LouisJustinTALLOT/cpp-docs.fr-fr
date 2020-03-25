---
title: Erreur de ligne de commande D8045
ms.date: 11/04/2016
f1_keywords:
- D8045
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
ms.openlocfilehash: 05a2d3851e58062e1e326781a223e2f4b0346620
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196844"
---
# <a name="command-line-error-d8045"></a>Erreur de ligne de commande D8045

Impossible de compiler le fichier C’fichier’avec l’option/clr

Seuls C++ les fichiers de code source peuvent être passés à une compilation qui utilise **/CLR**.  Utilisez **/TP** pour compiler un fichier. c en tant que fichier. cpp ; Pour plus d’informations, consultez [/TC,/TP,/TC,/TP (spécifier le type de fichier source)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) .

Pour plus d'informations, consultez [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

D8045 peut également se produire si vous compilez une application C++ATL à l’aide de Visual. Pour plus d’informations, consultez [Comment : effectuer une migration vers/CLR](../../dotnet/how-to-migrate-to-clr.md) .
