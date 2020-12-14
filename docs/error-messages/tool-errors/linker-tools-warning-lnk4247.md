---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4247'
title: Avertissement des outils Éditeur de liens LNK4247
ms.date: 11/04/2016
f1_keywords:
- LNK4247
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
ms.openlocfilehash: 88cd04e345b798b6927c3a5297380f1eeb3c5f5c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241181"
---
# <a name="linker-tools-warning-lnk4247"></a>Avertissement des outils Éditeur de liens LNK4247

le point d’entrée’decorated_function_name’a déjà un attribut de thread ; 'Attribute’ignoré

Un point d’entrée, spécifié avec [/entry (symbole de point d’entrée)](../../build/reference/entry-entry-point-symbol.md), avait un attribut de thread, mais [/CLRTHREADATTRIBUTE (définir l’attribut de thread CLR)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) a également été spécifié, avec un modèle de thread différent.

L’éditeur de liens a ignoré la valeur spécifiée avec/CLRTHREADATTRIBUTE.

Pour résoudre cet avertissement :

- Supprimez/CLRTHREADATTRIBUTE de votre Build.

- Supprimez l’attribut de votre fichier de code source.

- Supprimez à la fois l’attribut de la source et le/CLRTHREADATTRIBUTE de votre Build, puis acceptez le modèle de thread CLR par défaut.

- Modifiez la valeur passée à/CLRTHREADATTRIBUTE, de telle sorte qu’elle accepte l’attribut dans la source.

- Modifiez l’attribut dans source, de telle sorte qu’il accepte la valeur transmise à/CLRTHREADATTRIBUTE.

L’exemple suivant génère l’LNK4247

```cpp
// LNK4247.cpp
// compile with: /clr /c
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console
[System::MTAThreadAttribute]
void functionTitle (){}
```
