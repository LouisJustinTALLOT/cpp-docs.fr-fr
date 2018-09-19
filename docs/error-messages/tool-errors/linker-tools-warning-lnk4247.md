---
title: Avertissement LNK4247 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4247
dev_langs:
- C++
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d84a5964cb8df5d2973b6031da55d48dade584e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078008"
---
# <a name="linker-tools-warning-lnk4247"></a>Avertissement des outils Éditeur de liens LNK4247

point d’entrée 'nom_fonction_décoré' a déjà un attribut de thread ; 'attribute' ignoré

Un point d’entrée, spécifié avec [/ENTRY (symbole de Point d’entrée)](../../build/reference/entry-entry-point-symbol.md), possédait un attribut de thread, mais [/CLRTHREADATTRIBUTE (définir l’attribut de Thread CLR)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) également spécifié, avec un modèle de thread différent.

L’éditeur de liens a ignoré la valeur spécifiée avec /CLRTHREADATTRIBUTE.

Pour résoudre cet avertissement :

- Supprimez /CLRTHREADATTRIBUTE de votre build.

- Supprimez l’attribut à partir de votre fichier de code source.

- Retirez les deux l’attribut source et /CLRTHREADATTRIBUTE à partir de votre build et acceptez le modèle de thread CLR par défaut.

- Modifiez la valeur passée à /CLRTHREADATTRIBUTE., de sorte qu’elle correspond à l’attribut dans la source.

- Modifiez l’attribut dans la source, de sorte qu’elle accepte la valeur passée à /CLRTHREADATTRIBUTE.

L’exemple suivant génère l’erreur LNK4247

```
// LNK4247.cpp
// compile with: /clr /c
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console
[System::MTAThreadAttribute]
void functionTitle (){}
```