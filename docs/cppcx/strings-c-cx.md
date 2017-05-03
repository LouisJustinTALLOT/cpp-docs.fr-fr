---
title: "Cha&#238;nes (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
caps.latest.revision: 22
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 22
---
# Cha&#238;nes (C++/CX)
Le texte figurant dans le [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] est représenté dans [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] par la [Platform::String, classe](../cppcx/platform-string-class.md). Utilisez la `Platform::String Class` lorsque vous passez des chaînes dans les deux sens aux méthodes des classes [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] ou que vous interagissez avec d'autres composants [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] à travers la limite ABI \(Application Binary Interface\). La `Platform::String Class` fournit des méthodes pour plusieurs opérations de chaînes courantes mais elle n'est pas conçue pour être une classe de chaîne complète. Dans votre module C\+\+, utilisez les types de chaînes C\+\+ standard tels que [wstring](../Topic/wstring.md) pour tout traitement de texte significatif, puis convertissez le résultat final en [Platform::String^](../cppcx/platform-string-class.md) avant de le passer vers ou à partir d'une interface publique. Il est facile et efficace de convertir entre `wstring` ou `wchar_t*` et `Platform::String`.  
  
 **Passage rapide**  
  
 Dans certains cas, le compilateur peut vérifier qu'il peut sans risque construire une `Platform::String` ou passer une `String` à une fonction sans copier les données de chaîne sous\-jacentes. Ces opérations sont appelées *passage rapide* et elles se produisent de façon transparente.  
  
## Construction de chaînes  
 La valeur d'un objet `String` est une séquence \(en lecture seule\) immuable de caractères `char16` \(Unicode 16 bits\). Étant donné qu'un objet `String` est immuable, l'assignation d'un nouveau littéral de chaîne à une variable d' `String` remplace en fait l'objet d'origine `String` par un nouvel objet d' `String`. Les opérations de concaténation impliquent la destruction de l'objet `String` d'origine et la création d'un nouvel objet.  
  
 **Littéraux**  
  
 Un *caractère littéral* est un caractère placé entre guillemets simples et une *chaîne littérale* est une séquence de caractères placée entre guillemets doubles. Si vous utilisez un littéral pour initialiser une variable String^, le compilateur suppose que le littéral est constitué de caractères `char16`. Ainsi, vous ne devez pas faire précéder le littéral par le modificateur de chaîne « L » ou le placer dans une macro **\_T\(\)** ou **TEXT\(\)**. Pour plus d'informations sur la prise en charge de C\+\+ pour Unicode, consultez [Synthèse de la programmation Unicode](../text/unicode-programming-summary.md).  
  
 L'exemple suivant montre différentes façons de construire des objets `String`.  
  
 [!code-cpp[cx_strings#01](../snippets/cpp/VS_Snippets_Misc/cx_strings/cpp/class1.cpp#01)]  
  
## Opérations de gestion de chaînes  
 La classe `String` fournit des méthodes et des opérateurs pour la concaténation et comparaison de chaînes et d'autres opérations de base sur les chaînes. Pour effectuer d'autres manipulations plus étendues sur les chaînes, utilisez la fonction membre `String::Data()` pour récupérer la valeur de l'objet `String^` sous forme de `const wchar_t*`. Utilisez ensuite cette valeur pour initialiser un `std::wstring`, qui fournit des fonctions de gestion de chaînes évoluées.  
  
 [!code-cpp[cx_strings#03](../snippets/cpp/VS_Snippets_Misc/cx_strings/cpp/class1.cpp#03)]  
  
## Conversions de chaînes  
 Une `Platform::String` ne peut contenir que des caractères `char16` ou le caractère `NULL`. Si votre application doit utiliser les caractères 8 bits, servez\-vous de la [String::Data, méthode](../cppcx/string-data-method.md) pour récupérer le texte sous forme d'un `const wchar_t*`. Vous pouvez ensuite utiliser les fonctions Windows appropriées ou les fonctions de bibliothèque standard pour traiter les données et les reconvertir en un `wchar_t*` ou [wstring](../Topic/wstring.md), que vous pouvez utiliser pour construire une nouvelle `Platform::String`.  
  
 Le fragment de code suivant montre comment convertir une variable `String^` vers et à partir d'une variable `wstring`. Pour plus d'informations sur la manipulation de chaînes utilisée dans cet exemple, consultez [basic\_string::replace](../Topic/basic_string::replace.md).  
  
 [!code-cpp[cx_strings#04](../snippets/cpp/VS_Snippets_Misc/cx_strings/cpp/class1.cpp#04)]  
  
## Longueur de chaîne et valeurs NULL incorporées  
 La [String::Length, méthode](../cppcx/string-length-method.md) retourne le nombre de caractères de la chaîne au lieu du nombre d'octets. Le caractère NULL de fin n'est pas compté, sauf si vous le spécifiez explicitement lorsque vous utilisez la sémantique de pile pour construire une chaîne.  
  
 Une `Platform::String` peut contenir des valeurs NULL incorporées, mais uniquement lorsque NULL est le résultat d'une opération de concaténation. Les valeurs NULL incorporées ne sont pas prises en charge dans les littéraux de chaîne. Par conséquent, vous ne pouvez pas utiliser de valeurs NULL incorporées de cette manière pour initialiser une `Platform::String`. Les valeurs NULL incorporées dans une `Platform::String` sont ignorées lorsque la chaîne est affichée, par exemple lorsqu'elle est assignée à une propriété `TextBlock::Text`. Les valeurs NULL incorporées sont supprimées quand la valeur de chaîne est retournée par la propriété `Data`.  
  
## StringReference  
 Dans certains cas, votre code \(a\) reçoit std::wstring, une chaîne wchar\_t ou un littéral de chaîne L"", qu'il passe simplement à une autre méthode qui accepte String^ comme paramètre d'entrée. Tant que la mémoire tampon de chaîne d'origine elle\-même reste valide et qu'elle ne mute pas avant le retour de la fonction, vous pouvez convertir la chaîne ou le littéral de chaîne `wchar_t*` en [Platform::StringReference](../cppcx/platform-stringreference-class.md), et le passer à la place de `Platform::String^`. Cela est autorisé, car `StringReference` dispose d'une conversion définie par l'utilisateur en `Platform::String^`. À l'aide de `StringReference`, vous pouvez éviter d'effectuer une copie supplémentaire des données de chaîne. Dans les boucles où vous passez un grand nombre de chaînes, ou lorsque vous passez des chaînes de très grande taille, vous pouvez éventuellement obtenir une amélioration significative des performances à l'aide de `StringReference`. Toutefois, dans la mesure où `StringReference` emprunte essentiellement la mémoire tampon de chaîne d'origine, vous devez faire preuve d'une grande vigilance afin d'éviter une altération de la mémoire. Ne passez pas `StringReference` à une méthode asynchrone, à moins que la chaîne d'origine ne soit dans la portée lorsque cette méthode est retournée. Un String^ initialisé à partir de StringReference force l'allocation et la copie des données de chaîne, si une seconde opération d'affectation se produit. Dans ce cas, vous perdez le gain de performances fourni par `StringReference`.  
  
 Notez que `StringReference` est un type de classe C\+\+ standard, et non une classe ref. Vous ne pouvez pas l'utiliser dans l'interface publique des classes ref que vous définissez.  
  
 L'exemple suivant montre comment utiliser StringReference :  
  
```  
void GetDecodedStrings(std::vector<std::wstring> strings)  
{  
    using namespace Windows::Security::Cryptography;  
    using namespace Windows::Storage::Streams;  
  
    for (auto&& s : strings)  
    {  
        // Method signature is IBuffer^ CryptographicBuffer::DecodeFromBase64String (Platform::String^)  
        // Call using StringReference:  
        IBuffer^ buffer = CryptographicBuffer::DecodeFromBase64String(StringReference(s.c_str()));  
  
        //...do something with buffer  
    }  
}  
```  
  
## Voir aussi  
 [Built\-in Types](http://msdn.microsoft.com/fr-fr/acc196fd-09da-4882-b554-6c94685ec75f)