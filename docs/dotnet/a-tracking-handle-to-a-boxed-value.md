---
title: Handle de suivi d’une valeur Boxed | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- boxed value types, tracking handle to
ms.assetid: 16c92048-5b74-47d5-8eca-dfea3d38879a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c7e26efae93b509700c3bb0c992d9f397559e99f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380725"
---
# <a name="a-tracking-handle-to-a-boxed-value"></a>Handle de suivi d'une valeur boxed

L’utilisation d’un handle de suivi pour référencer un type valeur a changé d’Extensions managées pour C++ vers Visual C++.

Le boxing est une particularité du système de type CLR unifiée. Types valeur contiennent directement leur état, tandis que les types référence sont une paire implicite : l’entité nommée est un handle vers un objet sans nom alloué sur le tas managé. Toute initialisation ou assignation d’une valeur de type à un `Object`, par exemple, nécessite que le type de valeur soient placés dans le tas CLR - Voici où l’image d’une conversion boxing intervient - tout d’abord en allouant la mémoire associée, puis en copiant l’état de la valeur du type et puis de retourner l’adresse de cet hybride valeur/référence anonyme. Par conséquent, lorsqu’on écrit en c#

```cpp
object o = 1024; // C# implicit boxing
```

Il est beaucoup plus passe qu’est rendu visible par la simplicité du code. La conception de c# masque la complexité non seulement de quelles opérations sont effectuées sous le capot, mais également de l’abstraction d’une conversion boxing lui-même. Extensions managées pour C++, quant à eux, concerné que cela conduirait à un faux sentiment de l’efficacité, il place en face de l’utilisateur en requérant une instruction explicite :

```cpp
Object *o = __box( 1024 ); // Managed Extensions explicit boxing
```

Le boxing est implicite dans Visual C++ :

```cpp
Object ^o = 1024; // new syntax implicit boxing
```

Le `__box` mot clé sert d’un service essentiel au sein des Extensions managées, absent volontairement de langages tels que c# et Visual Basic : il fournit un vocabulaire et le suivi un handle pour manipuler directement une instance boxed sur le tas managé. Par exemple, considérez le petit programme suivant :

```cpp
int main() {
   double result = 3.14159;
   __box double * br = __box( result );

   result = 2.7;
   *br = 2.17;
   Object * o = br;

   Console::WriteLine( S"result :: {0}", result.ToString() ) ;
   Console::WriteLine( S"result :: {0}", __box(result) ) ;
   Console::WriteLine( S"result :: {0}", br );
}
```

Le code sous-jacent généré pour les trois appels de `WriteLine` afficher les différents coûts d’accès à la valeur d’une valeur boxed tapez (grâce à Yves Dolce pour ces différences), où les lignes indiquées affichent la surcharge associée à chaque appel.

```cpp
// Console::WriteLine( S"result :: {0}", result.ToString() ) ;
ldstr      "result :: {0}"
ldloca.s   result  // ToString overhead
call       instance string  [mscorlib]System.Double::ToString()  // ToString overhead
call       void [mscorlib]System.Console::WriteLine(string, object)

// Console::WriteLine( S"result :: {0}", __box(result) ) ;
Ldstr    " result :: {0}"
ldloc.0
box    [mscorlib]System.Double // box overhead
call    void [mscorlib]System.Console::WriteLine(string, object)

// Console::WriteLine( S"result :: {0}", br );
ldstr    "result :: {0}"
ldloc.0
call     void [mscorlib]System.Console::WriteLine(string, object)
```

En passant le type valeur boxed directement à `Console::WriteLine` élimine la conversion boxing et la nécessité d’appeler `ToString()`. (Bien sûr, il existe le boxing antérieures à initialiser `br`, de sorte que nous ne gagnons rien, sauf si nous mettons vraiment `br` fonctionne.

Dans la nouvelle syntaxe, la prise en charge pour les types valeur boxed est considérablement plus élégante et intégrée au sein du système de type tout en conservant sa puissance. Par exemple, voici la traduction de petit programme précédent :

```cpp
int main()
{
   double result = 3.14159;
   double^ br = result;
   result = 2.7;
   *br = 2.17;
   Object^ o = br;
   Console::WriteLine( "result :: {0}", result.ToString() );
   Console::WriteLine( "result :: {0}", result );
   Console::WriteLine( "result :: {0}", br );
}
```

## <a name="see-also"></a>Voir aussi

[Types valeur et leurs comportements (C++-CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Guide pratique pour demander explicitement le boxing](../dotnet/how-to-explicitly-request-boxing.md)