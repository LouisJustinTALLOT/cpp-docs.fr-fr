---
description: 'En savoir plus sur : considérations relatives à l’écriture de code de prologue/épilogue'
title: Considérations relatives à l’écriture de code Prolog-Epilog
ms.date: 11/04/2016
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
ms.openlocfilehash: 6deb6e9120c83992a7fe2529d0c9366b8e191056
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204769"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Considérations sur l'écriture de code de prologue/épilogue

**Spécifique à Microsoft**

Avant d’écrire vos propres séquences de code de prologue et d’épilogue, il est important de comprendre comment le frame de pile est disposé. Il est également utile de savoir comment utiliser le `__LOCAL_SIZE` symbole.

## <a name="stack-frame-layout"></a><a name="_pluslang_c.2b2b_.stack_frame_layout"></a> Disposition des frames de pile

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

## <a name="__local_size"></a><a name="_pluslang___local_size"></a> __LOCAL_SIZE

Le compilateur fournit un symbole, `__LOCAL_SIZE` , à utiliser dans le bloc assembleur inline du code de prologue de fonction. Ce symbole est utilisé pour allouer de l'espace pour les variables locales sur le frame de pile dans le code de prologue personnalisé.

Le compilateur détermine la valeur de `__LOCAL_SIZE` . Sa valeur représente le nombre total d'octets de toutes les variables locales définies par l'utilisateur et des variables temporaires générées par le compilateur. `__LOCAL_SIZE` peut être utilisé uniquement comme opérande immédiat ; elle ne peut pas être utilisée dans une expression. Vous ne devez pas modifier ou redéfinir la valeur de ce symbole. Par exemple :

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

L’exemple suivant d’une fonction Naked contenant des séquences de prologue et d’épilogue personnalisées utilise le `__LOCAL_SIZE` symbole dans la séquence de prologue :

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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Appels de fonction Naked](../cpp/naked-function-calls.md)
