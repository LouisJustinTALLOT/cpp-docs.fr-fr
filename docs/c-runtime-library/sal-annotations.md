---
title: Annotations SAL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __z annotation
- ref annotation
- _opt annotation
- __checkreturn annotatioin
- __deref_opt annotation
- deref_opt annotation
- __deref annotation
- __in annotation
- annotations [C++]
- z annotation
- _inout annotation
- __ref annotation
- full annotation
- _in annotation
- _ref annotation
- __out annotation
- _ecount annotation
- SAL annotations
- __opt annotation
- inout annotation
- in annotation
- _CA_SHOULD_CHECK_RETURN
- __bcount annotation
- _full annotation
- _bcount annotation
- deref annotation
- part annotation
- _out annotation
- __nz annotation
- __part annotation
- opt annotation
- __full annotation
- _nz annotation
- _z annotation
- out annotation
- __ecount annotation
- __inout annotation
- SAL annotations, _CA_SHOULD_CHECK_RETURN
- _deref_opt annotation
- _deref annotation
- nz annotation
- _part annotation
- ecount annotation
- bcount annotation
ms.assetid: 81893638-010c-41a0-9cb3-666fe360f3e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 363d7ff6de4c808c3c7b8d37a9a9f95bf069723c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107492"
---
# <a name="sal-annotations"></a>Annotations SAL

Si vous examinez les fichiers d'en-tête de bibliothèque, vous remarquerez peut-être des annotations inhabituelles, comme `_In_z` et `_Out_z_cap_(_Size)`. Voici des exemples de la langue d'annotation de code source Microsoft (SEL), qui fournit un ensemble d'annotations pour décrire comment une fonction utilise les paramètres, par exemple, les hypothèses qu'elle fait sur eux et les garanties qu'elle effectue sur le finissage. Le fichier d’en-tête \<sal.h> définit les annotations.

Pour plus d’informations sur l’utilisation d’annotations SAL dans Visual Studio, consultez [Utilisation d’annotations SAL pour réduire les défauts du code C/C++](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md)