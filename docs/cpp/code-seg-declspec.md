---
title: code_seg (__declspec)
ms.date: 11/04/2016
f1_keywords:
- code_seg_cpp
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
ms.openlocfilehash: a0b9c6dcd7ee19af59ac39a71498fe41bfc107ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506897"
---
# <a name="codeseg-declspec"></a>code_seg (__declspec)

**Section spécifique à Microsoft**

Le **code_seg** noms d’attribut de déclaration d’un segment de texte exécutable dans le fichier .obj dans lequel le code objet de la fonction ou les fonctions membres de classe est stocké.

## <a name="syntax"></a>Syntaxe

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>Notes

L'attribut `__declspec(code_seg(...))` permet de placer le code dans des blocs nommés distincts qui peuvent être paginés ou verrouillés individuellement en mémoire. Vous pouvez utiliser cet attribut pour contrôler l'emplacement des modèles instanciés et du code généré par le compilateur.

Un *segment* est un bloc nommé de données dans un fichier .obj qui est chargé en mémoire en tant qu’unité. Un *segment de texte* est un segment qui contient le code exécutable. Le terme *section* est synonyme de segment.

Le code objet qui est généré lorsque `declarator` est défini est placé dans le segment de texte spécifié par `segname`, qui est un littéral de chaîne étroite. Le nom `segname` ne doit pas être spécifié dans un [section](../preprocessor/section.md) pragma avant de pouvoir être utilisé dans une déclaration. Par défaut, lorsqu'aucun `code_seg` n'est spécifié, le code objet est placé dans un segment nommé ".text". Un **code_seg** attribut remplace tout existant [#pragma code_seg](../preprocessor/code-seg.md) directive. Un **code_seg** attribut appliqué à une fonction membre substitue à tout **code_seg** attribut appliqué à la classe englobante.

Si une entité présente un **code_seg** attribut, toutes les déclarations et définitions de la même entité doivent avoir identiques **code_seg** attributs. Si une classe de base a un **code_seg** attribut, dérivée de classes doivent avoir le même attribut.

Quand un **code_seg** l’attribut est appliqué à une fonction de la portée de l’espace de noms ou une fonction membre, le code objet de cette fonction est placé dans le segment de texte spécifié. Si cet attribut est appliqué à une classe, toutes les fonctions membres de la classe et des classes imbriquées (y compris les fonctions membres spéciales générées par le compilateur) sont placées dans le segment spécifié. Classes définies localement, par exemple, les classes définies dans un corps de la fonction membre — n’héritent pas les **code_seg** attribut de la portée englobante.

Quand un **code_seg** l’attribut est appliqué à une classe de modèle ou d’une fonction de modèle, toutes les spécialisations implicites du modèle sont placées dans le segment spécifié. Les spécialisations explicites ou partielles n’héritent pas les **code_seg** attribut à partir du modèle principal. Vous pouvez spécifier le même ou un autre **code_seg** attribut sur la spécialisation. Un **code_seg** attribut ne peut pas être appliqué à une instanciation explicite du modèle.

Par défaut, le code généré par le compilateur, tel qu'une fonction membre spéciale, est placé dans le segment ".text". La directive `#pragma code_seg` ne remplace pas cette valeur par défaut. Utilisez le **code_seg** attribut sur la classe, un modèle de classe ou un modèle de fonction pour contrôler l’emplacement du code généré par le compilateur.

Les expressions lambda héritent **code_seg** attributs à partir de leur portée englobante. Pour spécifier un segment pour une expression lambda, appliquez un **code_seg** attribut après la clause de déclaration de paramètre et avant tout autre mutable ou spécification d’exception, une spécification de type de retour de fin et le corps du lambda. Pour plus d’informations, consultez [syntaxe d’Expression Lambda](../cpp/lambda-expression-syntax.md). Cet exemple définit une expression lambda dans un segment nommé PagedMem :

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Faites attention lorsque vous placez des fonctions membres dans plusieurs segments, en particulier les fonctions membres virtuelles. Si vous définissez une fonction virtuelle dans une classe dérivée qui se trouve dans un segment paginé lorsque la méthode de la classe de base se trouve dans un segment non paginé, les autres méthodes de la classe de base ou le code utilisateur peuvent supposer que l'appel de la méthode virtuelle ne génèrera pas de défaut de page.

## <a name="example"></a>Exemple

Cet exemple montre comment un **code_seg** contrôles de l’attribut emplacement des segments lorsqu’implicite et la spécialisation de modèle explicite est utilisée :

```cpp
// code_seg.cpp
// Compile: cl /EHsc /W4 code_seg.cpp

// Base template places object code in Segment_1 segment
template<class T>
class __declspec(code_seg("Segment_1")) Example
{
public:
   virtual void VirtualMemberFunction(T /*arg*/) {}
};

// bool specialization places code in default .text segment
template<>
class Example<bool>
{
public:
   virtual void VirtualMemberFunction(bool /*arg*/) {}
};

// int specialization places code in Segment_2 segment
template<>
class __declspec(code_seg("Segment_2")) Example<int>
{
public:
   virtual void VirtualMemberFunction(int /*arg*/) {}
};

// Compiler warns and ignores __declspec(code_seg("Segment_3"))
// in this explicit specialization
__declspec(code_seg("Segment_3")) Example<short>; // C4071

int main()
{
   // implicit double specialization uses base template's
   // __declspec(code_seg("Segment_1")) to place object code
   Example<double> doubleExample{};
   doubleExample.VirtualMemberFunction(3.14L);

   // bool specialization places object code in default .text segment
   Example<bool> boolExample{};
   boolExample.VirtualMemberFunction(true);

   // int specialization uses __declspec(code_seg("Segment_2"))
   // to place object code
   Example<int> intExample{};
   intExample.VirtualMemberFunction(42);
}
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)