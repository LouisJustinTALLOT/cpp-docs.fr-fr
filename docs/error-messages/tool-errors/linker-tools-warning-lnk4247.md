---
title: Avertissement des outils Éditeur de liens LNK4247
ms.date: 11/04/2016
f1_keywords:
- LNK4247
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
ms.openlocfilehash: cd4108f8bd06ec7a0b2d2eb9fab13917174b797b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516023"
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