---
description: 'En savoir plus sur : `__asm`'
title: __asm
ms.date: 10/09/2018
f1_keywords:
- __asm
- _asm
- __asm_cpp
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
ms.openlocfilehash: 5fa4e64bdb9ae4fc01e6e379de3e8a6771959e80
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118054"
---
# `__asm`

**Spécifique à Microsoft**

Le **`__asm`** mot clé appelle l’assembleur inline et peut apparaître partout où une instruction C ou C++ est légale. Il ne peut pas apparaître de lui-même. Il doit être suivi par une instruction assembleur, un groupe d'instructions entre accolades ou, au minimum, par une paire d'accolades vide. Ici, le terme « **`__asm`** bloc » fait référence à toute instruction ou à tout groupe d’instructions, qu’elles soient ou non placées entre accolades.

> [!NOTE]
> Visual C++ la prise en charge du **`asm`** mot clé C++ standard est limitée au fait que le compilateur ne génère pas d’erreur sur le mot clé. Toutefois, un **`asm`** bloc ne génère pas de code significatif. Utilisez à la **`__asm`** place de **`asm`** .

## <a name="grammar"></a>Grammaire

*bloc asm*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm`***assembly-instruction* **`;`** <sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm {`***assembly-instruction-List* **`}`** **`;`** <sub>OPT</sub>

*assembly-instruction-List*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-instruction* **`;`** <sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-instruction* **`;`** *assembly-instruction-List* **`;`** <sub>OPT</sub>

## <a name="remarks"></a>Notes

S’il est utilisé sans accolades, le **`__asm`** mot clé signifie que le reste de la ligne est une instruction en langage assembleur. Utilisé avec les accolades, il signifie que chaque ligne entre accolades est une instruction en langage assembleur. Pour la compatibilité avec les versions précédentes, **`_asm`** est un synonyme de **`__asm`** .

Étant donné que le **`__asm`** mot clé est un séparateur d’instruction, vous pouvez placer des instructions d’assembly sur la même ligne.

Avant Visual Studio 2005, l’instruction

```cpp
__asm int 3
```

n’a pas provoqué la génération de code natif lors de la compilation avec **/CLR**; le compilateur a traduit l’instruction en une instruction de rupture CLR.

`__asm int 3` entraîne maintenant la génération de code natif pour la fonction. Si vous souhaitez qu’une fonction génère un point d’arrêt dans votre code et que vous souhaitiez que cette fonction soit compilée en langage MSIL, utilisez [__debugbreak](../../intrinsics/debugbreak.md).

Pour la compatibilité avec les versions précédentes, **`_asm`** est un synonyme de, **`__asm`** sauf si l’option de compilateur [/za \( Désactiver les extensions de langage)](../../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

## <a name="example"></a>Exemple

Le fragment de code suivant est un simple **`__asm`** bloc entre accolades :

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

Vous pouvez également placer **`__asm`** devant chaque instruction d’assembly :

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

Étant donné que le **`__asm`** mot clé est un séparateur d’instruction, vous pouvez également placer des instructions d’assembly sur la même ligne :

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

Les trois exemples génèrent le même code, mais le premier style (englobant le **`__asm`** bloc entre accolades) présente des avantages. Les accolades séparent clairement le code assembleur du code C ou C++ et évitent toute répétition inutile du **`__asm`** mot clé. Les accolades peuvent également empêcher les ambiguïtés. Si vous souhaitez placer une instruction C ou C++ sur la même ligne qu’un **`__asm`** bloc, vous devez placer le bloc entre accolades. Sans accolades, le compilateur ne peut pas savoir où le code assembleur s'arrête et où les instructions C ou C++ démarrent. Enfin, étant donné que le texte entre accolades a le même format que le texte MASM ordinaire, vous pouvez facilement couper et coller le texte depuis des fichiers sources MASM existants.

Contrairement aux accolades en C et C++, les accolades englobant un **`__asm`** bloc n’affectent pas la portée de la variable. Vous pouvez également imbriquer des **`__asm`** blocs ; l’imbrication n’affecte pas la portée des variables.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../../cpp/keywords-cpp.md)<br/>
[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>
