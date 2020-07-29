---
title: Modèles de fonctions
ms.date: 07/15/2019
helpviewer_keywords:
- function templates
- templates, function
- function templates, about function templates
ms.assetid: 59b56a4b-0689-4161-9c07-25021562e2a7
ms.openlocfilehash: 44fb8691c296892377686310fbd9b4d9adcd0f80
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232285"
---
# <a name="function-templates"></a>Modèles de fonctions

Les modèles de classe définissent une famille de classes connexes basées sur les arguments de type passés à la classe lors de son instanciation. Les modèles de fonction sont semblables aux modèles de classe mais définissent une famille de fonctions. Avec les modèles de fonction, vous pouvez spécifier un ensemble de fonctions basées sur le même code mais agir sur différents types ou différentes classes. Le modèle de fonction suivant permute deux éléments :

```cpp
// function_templates1.cpp
template< class T > void MySwap( T& a, T& b ) {
   T c(a);
   a = b;
   b = c;
}
int main() {
}
```

Ce code définit une famille de fonctions qui permutent les valeurs des arguments. À partir de ce modèle, vous pouvez générer des fonctions qui échangent **`int`** les **`long`** types et, ainsi que les types définis par l’utilisateur. `MySwap` permutera même une classe si le constructeur de copie et l'opérateur d'assignation de cette classe sont correctement définis.

En outre, le modèle de fonction vous empêchera de permuter les objets de types différents, car le compilateur connaît les types des paramètres a et *b* au moment de *la* compilation.

Bien que cette fonction puisse être effectuée par une fonction non basée sur un modèle à l'aide de pointeurs void, la version de modèle est de type sécurisé. Prenons les appels suivants :

```cpp
int j = 10;
int k = 18;
CString Hello = "Hello, Windows!";
MySwap( j, k );          //OK
MySwap( j, Hello );      //error
```

Le deuxième appel `MySwap` déclenche une erreur au moment de la compilation, car le compilateur ne peut pas générer de fonction `MySwap` avec des paramètres de types différents. Si des pointeurs void étaient utilisés, les deux appels de fonction se compileraient correctement, mais la fonction ne fonctionnerait pas correctement au moment de l'exécution.

Il est autorisé de spécifier explicitement les arguments template d'un modèle de fonction. Par exemple :

```cpp
// function_templates2.cpp
template<class T> void f(T) {}
int main(int j) {
   f<char>(j);   // Generate the specialization f(char).
   // If not explicitly specified, f(int) would be deduced.
}
```

Lorsque l’argument template est spécifié explicitement, les conversions implicites normales sont effectuées pour convertir l’argument de fonction vers le type des paramètres de modèle de fonction correspondants. Dans l’exemple ci-dessus, le compilateur est converti `j` en type **`char`** .

## <a name="see-also"></a>Voir aussi

[Modèles](../cpp/templates-cpp.md)<br/>
[Instanciation de modèle de fonction](../cpp/function-template-instantiation.md)<br/>
[Instanciation explicite](../cpp/explicit-instantiation.md)<br/>
[Spécialisation explicite des modèles de fonction](../cpp/explicit-specialization-of-function-templates.md)
