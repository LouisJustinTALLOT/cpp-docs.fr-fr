---
title: Problèmes courants de migration vers Visual C++ 64 bits
ms.date: 05/06/2019
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
ms.openlocfilehash: 68f4dc4276c5cbce687477ca25ec69f0cb544acb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229855"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Problèmes courants de migration vers Visual C++ 64 bits

Lorsque vous utilisez le compilateur Microsoft C++ (MSVC) pour créer des applications qui s’exécutent sur un système d’exploitation Windows 64 bits, vous devez être conscient des problèmes suivants :

- Un **`int`** et un **`long`** sont des valeurs 32 bits sur les systèmes d’exploitation Windows 64 bits. Pour les programmes que vous prévoyez de compiler pour des plateformes 64 bits, veillez à ne pas assigner de pointeurs à des variables 32 bits. Les pointeurs sont des valeurs 64 bits sur les plateformes 64 bits et vous tronquerez la valeur d'un pointeur si vous l'assignez à une variable 32 bits.

- `size_t`, `time_t` et `ptrdiff_t` sont des valeurs 64 bits sur les systèmes d’exploitation Windows 64 bits.

- `time_t`est une valeur 32 bits sur les systèmes d’exploitation Windows 32 bits dans Visual Studio 2005 et versions antérieures. `time_t` est maintenant un entier 64 bits par défaut. Pour plus d’informations, consultez [gestion du temps](../c-runtime-library/time-management.md).

   Vous devez être conscient de l’endroit où votre code prend une **`int`** valeur et le traite en tant que `size_t` `time_t` valeur ou. Il est possible que le nombre puisse croître pour être plus grand qu’un nombre 32 bits et que les données soient tronquées lorsqu’elles sont renvoyées au **`int`** stockage.

Le modificateur% x ( **`int`** format hexadécimal) ne `printf` fonctionne pas comme prévu sur un système d’exploitation Windows 64 bits. Il ne fonctionne que sur les 32 premiers bits de la valeur qui lui est passée.

- Utilisez %I32x pour afficher un type intégral 32 bits au format hexadécimal.

- Utilisez %I64x pour afficher un type intégral 64 bits au format hexadécimal.

- Le %p (format hexadécimal pour un pointeur) fonctionnera comme prévu sur un système d'exploitation Windows 64 bits.

Pour plus d'informations, consultez les pages suivantes :

- [Options du compilateur MSVC](reference/compiler-options.md)

- [Conseils de migration](/windows/win32/WinProg64/migration-tips)

## <a name="see-also"></a>Voir aussi

[Configurer des projets C++ pour des cibles x64 64 bits](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Guide du portage et de la mise à niveau de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)
