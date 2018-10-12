---
title: __asm | Microsoft Docs
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- __asm
- _asm
- __asm_cpp
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd279a6324aec6eba50c6c3b7ffe846200d45fe1
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161721"
---
# <a name="asm"></a>__asm

**Section spécifique à Microsoft**

Le mot clé `__asm` appelle l'assembleur inline et peut apparaître partout où une instruction C ou C++ est conforme. Il ne peut pas apparaître de lui-même. Il doit être suivi par une instruction assembleur, un groupe d'instructions entre accolades ou, au minimum, par une paire d'accolades vide. Le terme « bloc `__asm`  » fait ici référence à une instruction ou un groupe d'instructions, que ce dernier soit ou non entouré d'accolades.

> [!NOTE]
> La prise en charge du mot clé C++ standard `asm` par Visual C++ se limite au fait que le compilateur ne génère pas d'erreur pour le mot clé. Toutefois, un bloc `asm` ne génère aucun code explicite. Utilisez `__asm` à la place de `asm`.

## <a name="grammar"></a>Grammaire

*bloc asm*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm** *instruction d’assembly* **;** <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {** *liste d’instructions d’assembly* **}** **;** <sub>opt</sub>

*liste d’instructions d’assembly*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction d’assembly* **;** <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction d’assembly* **;** *liste d’instructions d’assembly* **;** <sub>opt</sub>

## <a name="remarks"></a>Notes

Utilisé sans accolades, le mot clé `__asm` signifie que le reste de la ligne est une instruction en langage assembleur. Utilisé avec les accolades, il signifie que chaque ligne entre accolades est une instruction en langage assembleur. Pour assurer la compatibilité avec les versions antérieures, `_asm` est un synonyme de `__asm`.

Dans la mesure où le mot clé `__asm` est un séparateur d'instruction, vous pouvez placer des instructions assembleur sur la même ligne :

Avant Visual C++ 2005, l'instruction

```cpp
__asm int 3
```

n’a pas entraîné de code natif doit être généré lors de la compilation avec **/CLR**; le compilateur a traduit l’instruction à une instruction de saut CLR.

`__asm int 3` entraîne maintenant la génération de code natif pour la fonction. Si vous voulez que la fonction génèrent un point d’arrêt dans votre code et si vous souhaitez qu’elle soit compilée en langage MSIL, utilisez [__debugbreak](../../intrinsics/debugbreak.md).

Pour assurer la compatibilité avec les versions précédentes, **_asm ne** est un synonyme de **__asm** , sauf si option du compilateur [/Za \(désactiver les extensions de langage)](../../build/reference/za-ze-disable-language-extensions.md) est spécifié.

## <a name="example"></a>Exemple

Le fragment de code suivant est un simple bloc `__asm` entre accolades :

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

Vous pouvez aussi placer `__asm` devant chaque instruction assembleur :

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

Le mot clé `__asm` étant un séparateur d'instruction, vous pouvez également insérer des instructions assembleur sur la même ligne :

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

Les trois exemples génèrent le même code, mais le premier style (bloc `__asm` placé entre accolades) présente quelques avantages. Les accolades séparent clairement le code de l'assembly du code C ou C++. De plus, elles évitent toute répétition inutile du mot clé `__asm`. Les accolades peuvent également empêcher les ambiguïtés. Pour placer une instruction C ou C++ sur la même ligne qu'un bloc `__asm`, placez le bloc entre accolades. Sans accolades, le compilateur ne peut pas savoir où le code assembleur s'arrête et où les instructions C ou C++ démarrent. Enfin, étant donné que le texte entre accolades a le même format que le texte MASM ordinaire, vous pouvez facilement couper et coller le texte depuis des fichiers sources MASM existants.

Contrairement aux accolades en C et C++, celles encadrant un bloc `__asm` n'affectent pas la portée de la variable. Vous pouvez également imbriquer les blocs `__asm` ; l'imbrication n'affecte pas la portée de la variable.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../../cpp/keywords-cpp.md)<br/>
[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>