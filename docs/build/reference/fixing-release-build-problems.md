---
title: Correction de mise en production de Build | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- release builds, troubleshooting
- debug builds, memory overwrites
- memory, overwrites
- troubleshooting Visual C++, release builds
- troubleshooting release builds
ms.assetid: a0c0818e-4c47-4fe0-a611-50d61a41bd88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9b304fa6bcc9b0b248719ea44b28e9dae5c76a6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726529"
---
# <a name="fixing-release-build-problems"></a>Résolution de problèmes liés à la version release

Si votre code génère des erreurs de compilation après basculement à partir de la version debug pour la version Release, il existe certaines zones, que vous devez vérifier.

Vous pouvez recevoir des avertissements du compilateur lors d’une génération optimisée (version) que vous n’avez pas reçu au cours d’une version debug.

- [Examiner les instructions ASSERT](../../build/reference/using-verify-instead-of-assert.md)

- [Utiliser la version Debug pour vérifier pour les remplacements de mémoire](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)

- [Activer la génération d’informations de débogage pour la version Release](../../build/reference/how-to-debug-a-release-build.md)

- [Vérification des remplacements de mémoire](../../build/reference/checking-for-memory-overwrites.md)

## <a name="see-also"></a>Voir aussi

[Versions Release](../../build/reference/release-builds.md)<br/>
[Problèmes courants lors de la création d’une version Release](../../build/reference/common-problems-when-creating-a-release-build.md)<br/>
[Optimisation du code](../../build/reference/optimizing-your-code.md)