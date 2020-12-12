---
description: 'En savoir plus sur : erreur Command-Line D8045'
title: Erreur de ligne de commande D8045
ms.date: 11/04/2016
f1_keywords:
- D8045
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
ms.openlocfilehash: 0445454a1e44e85b43fa0302867d9109e9ee3e38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115597"
---
# <a name="command-line-error-d8045"></a>Erreur de ligne de commande D8045

Impossible de compiler le fichier C’fichier’avec l’option/clr

Seuls les fichiers de code source C++ peuvent être passés à une compilation qui utilise **/CLR**.  Utilisez **/TP** pour compiler un fichier. c en tant que fichier. cpp ; Pour plus d’informations, consultez [/TC,/TP,/TC,/TP (spécifier le type de fichier source)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) .

Pour plus d’informations, consultez [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

D8045 peut également se produire si vous compilez une application ATL à l’aide de Visual C++. Pour plus d’informations, consultez [Comment : effectuer une migration vers/CLR](../../dotnet/how-to-migrate-to-clr.md) .
