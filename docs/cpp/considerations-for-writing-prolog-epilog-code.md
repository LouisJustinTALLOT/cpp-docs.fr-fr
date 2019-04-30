---
title: Considérations sur l’écriture de Code de prologue / épilogue
ms.date: 11/04/2016
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
ms.openlocfilehash: a70c444af9e1622b3f46837fcfa2d5e8856abf30
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399133"
---
# <a name="considerations-for-writing-prologepilog-code"></a>Considérations sur l'écriture de code de prologue/épilogue

**Section spécifique à Microsoft**

Avant d'écrire vos propres séquences de code de prologue et d'épilogue, il importe de comprendre comment le frame de pile est disposé. Il est également utile de savoir comment utiliser le `__LOCAL_SIZE` symbole.

##  <a name="_pluslang_c.2b2b_.stack_frame_layout"></a> Disposition du Frame de pile

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

##  <a name="_pluslang___local_size"></a> __LOCAL_SIZE

Le compilateur fournit un symbole, `__LOCAL_SIZE`, pour une utilisation dans le bloc assembleur inline de code de prologue de fonction. Ce symbole est utilisé pour allouer de l'espace pour les variables locales sur le frame de pile dans le code de prologue personnalisé.

Le compilateur détermine la valeur de `__LOCAL_SIZE`. Sa valeur représente le nombre total d'octets de toutes les variables locales définies par l'utilisateur et des variables temporaires générées par le compilateur. `__LOCAL_SIZE` peut être utilisé uniquement comme opérande immédiat. Il ne peut pas être utilisé dans une expression. Vous ne devez pas modifier ou redéfinir la valeur de ce symbole. Exemple :

```
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov        eax, [ebp - __LOCAL_SIZE]   ;Error
```

L’exemple suivant d’une fonction naked contenant personnalisé prologue et épilogue séquences utilise le `__LOCAL_SIZE` symbole dans la séquence de prologue :

```
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

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Appels de fonction naked](../cpp/naked-function-calls.md)