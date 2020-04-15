---
title: Considérations sur l’écriture de code de prologue/épilogue
ms.date: 11/04/2016
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
ms.openlocfilehash: cda6a6c82efcf30a916aced121024095d7ce8138
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337110"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Considérations sur l'écriture de code de prologue/épilogue

**Microsoft Spécifique**

Avant d’écrire vos propres séquences de code prolog et épilog, il est important de comprendre comment le cadre de pile est disposé. Il est également utile de `__LOCAL_SIZE` savoir comment utiliser le symbole.

## <a name="stack-frame-layout"></a><a name="_pluslang_c.2b2b_.stack_frame_layout"></a>Mise en page du cadre de pile

Cet exemple montre le code de prologue standard qui peut apparaître dans une fonction 32 bits :

```
push        ebp                ; Save ebp
mov         ebp, esp           ; Set stack frame pointer
sub         esp, localbytes    ; Allocate space for locals
push        <registers>        ; Save registers
```

La variable `localbytes` représente le nombre d'octets nécessaires sur la pile pour les variables locales. La variable `<registers>` est un espace réservé qui représente la liste de registres à enregistrer sur la pile. Après avoir effectué un push des registres, vous pouvez placer toutes les autres données pertinentes sur la pile. Voici le code d'épilogue correspondant :

```
pop         <registers>   ; Restore registers
mov         esp, ebp      ; Restore stack pointer
pop         ebp           ; Restore ebp
ret                       ; Return from function
```

La pile se réduit toujours (des adresses de mémoire supérieures aux adresses de mémoire inférieures). Le pointeur de base (`ebp`) pointe vers la valeur de `ebp` qui fait l'objet d'un push. La zone Variables locales commence à `ebp-4`. Pour accéder aux variables locales, calculez un décalage à partir de `ebp` en soustrayant la valeur appropriée de `ebp`.

## <a name="__local_size"></a><a name="_pluslang___local_size"></a>__LOCAL_SIZE

Le compilateur fournit `__LOCAL_SIZE`un symbole, pour une utilisation dans le bloc d’assembleur en ligne du code prolog de fonction. Ce symbole est utilisé pour allouer de l'espace pour les variables locales sur le frame de pile dans le code de prologue personnalisé.

Le compilateur détermine la `__LOCAL_SIZE`valeur de . Sa valeur représente le nombre total d'octets de toutes les variables locales définies par l'utilisateur et des variables temporaires générées par le compilateur. `__LOCAL_SIZE`ne peut être utilisé que comme un opératment immédiat; il ne peut pas être utilisé dans une expression. Vous ne devez pas modifier ou redéfinir la valeur de ce symbole. Par exemple :

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

L’exemple suivant d’une fonction nue contenant des `__LOCAL_SIZE` séquences de prolog et d’épilogie personnalisées utilise le symbole dans la séquence prolog :

```cpp
// the__local_size_symbol.cpp
// processor: x86
__declspec ( naked ) int main() {
   int i;
   int j;

   __asm {      /* prolog */
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */
   __asm {   /* epilog */
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**END Microsoft Spécifique**

## <a name="see-also"></a>Voir aussi

[Appels de fonction naked](../cpp/naked-function-calls.md)
