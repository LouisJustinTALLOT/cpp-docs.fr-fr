---
title: Avertissement des outils Éditeur de liens LNK4247
ms.date: 11/04/2016
f1_keywords:
- LNK4247
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
ms.openlocfilehash: 344c219fa1f3daa1e5f9c31431e608f5e7036400
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991151"
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
