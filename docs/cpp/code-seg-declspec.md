---
description: 'En savoir plus sur les éléments suivants : code_seg (__declspec)'
title: code_seg (__declspec)
ms.date: 11/04/2016
f1_keywords:
- code_seg_cpp
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
ms.openlocfilehash: b382e0a758c28ffab297badda7670c1de3b08d32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171089"
---
# <a name="code_seg-__declspec"></a>code_seg (__declspec)

**Spécifique à Microsoft**

L’attribut de Déclaration **code_seg** nomme un segment de texte exécutable dans le fichier. obj dans lequel le code objet des fonctions membres de la fonction ou de la classe sera stocké.

## <a name="syntax"></a>Syntaxe

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>Notes

L'attribut `__declspec(code_seg(...))` permet de placer le code dans des blocs nommés distincts qui peuvent être paginés ou verrouillés individuellement en mémoire. Vous pouvez utiliser cet attribut pour contrôler l'emplacement des modèles instanciés et du code généré par le compilateur.

Un *segment* est un bloc de données nommé dans un fichier. obj qui est chargé en mémoire en tant qu’unité. Un *segment de texte* est un segment qui contient du code exécutable. La *section* term est souvent utilisée de façon interchangeable avec segment.

Le code objet qui est généré lorsque `declarator` est défini est placé dans le segment de texte spécifié par `segname`, qui est un littéral de chaîne étroite. Le nom `segname` ne doit pas être spécifié dans un pragma de [section](../preprocessor/section.md) avant de pouvoir être utilisé dans une déclaration. Par défaut, lorsqu'aucun `code_seg` n'est spécifié, le code objet est placé dans un segment nommé ".text". Un attribut **code_seg** remplace toute directive [code_seg #pragma](../preprocessor/code-seg.md) existante. Un attribut **code_seg** appliqué à une fonction membre remplace tout attribut **code_seg** appliqué à la classe englobante.

Si une entité a un attribut **code_seg** , toutes les déclarations et définitions de la même entité doivent avoir des attributs **code_seg** identiques. Si une classe de base a un attribut **code_seg** , les classes dérivées doivent avoir le même attribut.

Lorsqu’un attribut **code_seg** est appliqué à une fonction de portée espace de noms ou à une fonction membre, le code objet de cette fonction est placé dans le segment de texte spécifié. Si cet attribut est appliqué à une classe, toutes les fonctions membres de la classe et des classes imbriquées (y compris les fonctions membres spéciales générées par le compilateur) sont placées dans le segment spécifié. Les classes définies localement (par exemple, les classes définies dans un corps de fonction membre) n’héritent pas de l’attribut **code_seg** de la portée englobante.

Lorsqu’un attribut **code_seg** est appliqué à une classe de modèle ou à une fonction de modèle, toutes les spécialisations implicites du modèle sont placées dans le segment spécifié. Les spécialisations explicites ou partielles n’héritent pas de l’attribut **code_seg** du modèle principal. Vous pouvez spécifier le même attribut ou un autre **code_seg** sur la spécialisation. Un attribut **code_seg** ne peut pas être appliqué à une instanciation de modèle explicite.

Par défaut, le code généré par le compilateur, tel qu'une fonction membre spéciale, est placé dans le segment ".text". La directive `#pragma code_seg` ne remplace pas cette valeur par défaut. Utilisez l’attribut **code_seg** sur la classe, le modèle de classe ou le modèle de fonction pour contrôler l’emplacement où le code généré par le compilateur est placé.

Les expressions lambda héritent **code_seg** attributs de la portée englobante. Pour spécifier un segment pour une expression lambda, appliquez un attribut **code_seg** après la clause Parameter-DECLARATION et avant toute spécification mutable ou d’exception, toute spécification de type de retour de fin et le corps de l’expression lambda. Pour plus d’informations, consultez [syntaxe d’expression lambda](../cpp/lambda-expression-syntax.md). Cet exemple définit une expression lambda dans un segment nommé PagedMem :

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Faites attention lorsque vous placez des fonctions membres dans plusieurs segments, en particulier les fonctions membres virtuelles. Si vous définissez une fonction virtuelle dans une classe dérivée qui se trouve dans un segment paginé lorsque la méthode de la classe de base se trouve dans un segment non paginé, les autres méthodes de la classe de base ou le code utilisateur peuvent supposer que l'appel de la méthode virtuelle ne génèrera pas de défaut de page.

## <a name="example"></a>Exemple

Cet exemple montre comment un attribut **code_seg** contrôle l’emplacement d’un segment lorsque la spécialisation de modèle implicite et explicite est utilisée :

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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
