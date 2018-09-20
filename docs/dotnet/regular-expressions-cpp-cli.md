---
title: Les Expressions régulières (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular expressions [C++]
- .NET Framework [C++], regular expressions
- regular expressions [C++], about regular expressions
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- Split method, parsing strings
- strings [C++], parsing
- substrings, simple matches
- searching, exact substring matches
- strings [C++], exact substring matching
- regular expressions [C++], simple matching
- IsMatch method
- strings [C++], extracting data from
- formatted strings [C++]
- regular expressions [C++], extracting data fields
- data [C++], extracting from strings
- regular expressions [C++], rearranging data
- data [C++], rearranging
- search and replace
- Replace method
- regular expressions [C++], search and replace
- strings [C++], formatting
- data [C++], formatting
- regular expressions [C++], validating data formatting
ms.assetid: 838bab49-0dbc-4089-a604-ef146269ef5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7f9937d9f93af6179d890f1e9160dd8900cd9f14
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375613"
---
# <a name="regular-expressions-ccli"></a>Expressions régulières (C++/CLI)

Illustre diverses opérations de chaîne à l’aide des classes d’expressions régulières dans le .NET Framework.

Les rubriques suivantes illustrent l’utilisation du .NET Framework <xref:System.Text.RegularExpressions> espace de noms (et dans un cas le <xref:System.String.Split%2A?displayProperty=fullName> méthode) pour rechercher, analyser et modifier des chaînes.

## <a name="parse_regex"></a> Analyser des chaînes à l’aide d’Expressions régulières

L’exemple de code suivant illustre l’analyse de chaîne simple à l’aide de la <xref:System.Text.RegularExpressions.Regex> classe dans le <xref:System.Text.RegularExpressions?displayProperty=fullName> espace de noms. Chaîne qui contient plusieurs types de délimiteurs de word est construite. Elle est analysée à l’aide de la <xref:System.Text.RegularExpressions.Regex> classe conjointement avec la <xref:System.Text.RegularExpressions.Match> classe. Ensuite, chaque mot dans la phrase est affiché séparément.

### <a name="example"></a>Exemple

```cpp
// regex_parse.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main( )
{
   int words = 0;
   String^ pattern = "[a-zA-Z]*";
   Console::WriteLine( "pattern : '{0}'", pattern );
   Regex^ regex = gcnew Regex( pattern );

   String^ line = "one\ttwo three:four,five six  seven";
   Console::WriteLine( "text : '{0}'", line );
   for( Match^ match = regex->Match( line );
        match->Success; match = match->NextMatch( ) )
   {
      if( match->Value->Length > 0 )
      {
         words++;
         Console::WriteLine( "{0}", match->Value );
      }
   }
   Console::WriteLine( "Number of Words : {0}", words );

   return 0;
}
```

## <a name="parse_split"></a> Analyser des chaînes à l’aide de la méthode Split

L’exemple de code suivant montre comment utiliser le <xref:System.String.Split%2A?displayProperty=fullName> méthode pour extraire chaque mot d’une chaîne. Chaîne qui contient plusieurs types de délimiteurs de word est construite, puis analysée en appelant <xref:System.String.Split%2A> avec une liste des délimiteurs des. Ensuite, chaque mot dans la phrase est affiché séparément.

### <a name="example"></a>Exemple

```cpp
// regex_split.cpp
// compile with: /clr
using namespace System;

int main()
{
   String^ delimStr = " ,.:\t";
   Console::WriteLine( "delimiter : '{0}'", delimStr );
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ words;
   String^ line = "one\ttwo three:four,five six seven";

   Console::WriteLine( "text : '{0}'", line );
   words = line->Split( delimiter );
   Console::WriteLine( "Number of Words : {0}", words->Length );
   for (int word=0; word<words->Length; word++)
      Console::WriteLine( "{0}", words[word] );

   return 0;
}
```

## <a name="regex_simple"></a> Utiliser des Expressions régulières pour la correspondance Simple

L’exemple de code suivant utilise des expressions régulières pour rechercher des correspondances de sous-chaînes exactes. La recherche est effectuée par la méthode statique <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> (méthode), qui prend deux chaînes en tant qu’entrée. La première est la chaîne à rechercher, et le second est le modèle à rechercher.

### <a name="example"></a>Exemple

```cpp
// regex_simple.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
   array<String^>^ sentence =
   {
      "cow over the moon",
      "Betsy the Cow",
      "cowering in the corner",
      "no match here"
   };

   String^ matchStr = "cow";
   for (int i=0; i<sentence->Length; i++)
   {
      Console::Write( "{0,24}", sentence[i] );
      if ( Regex::IsMatch( sentence[i], matchStr,
                     RegexOptions::IgnoreCase ) )
         Console::WriteLine("  (match for '{0}' found)", matchStr);
      else
         Console::WriteLine("");
   }
   return 0;
}
```

## <a name="regex_extract"></a> Utiliser des Expressions régulières pour extraire des champs de données

L’exemple de code suivant illustre l’utilisation d’expressions régulières pour extraire des données à partir d’une chaîne mise en forme. Le code suivant exemple utilise le <xref:System.Text.RegularExpressions.Regex> classe pour spécifier un modèle qui correspond à une adresse de messagerie. Ce modèle inclut des identificateurs de champ qui peuvent être utilisées pour récupérer les parties de nom d’hôte de chaque adresse de messagerie. Le <xref:System.Text.RegularExpressions.Match> classe est utilisée pour effectuer la correspondance de modèle réelle. Si l’adresse de messagerie donnée est valide, le nom d’utilisateur et les noms d’hôte sont extraites et affichées.

### <a name="example"></a>Exemple

```cpp
// Regex_extract.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
    array<String^>^ address=
    {
        "jay@southridgevideo.com",
        "barry@adatum.com",
        "treyresearch.net",
        "karen@proseware.com"
    };

    Regex^ emailregex = gcnew Regex("(?<user>[^@]+)@(?<host>.+)");

    for (int i=0; i<address->Length; i++)
    {
        Match^ m = emailregex->Match( address[i] );
        Console::Write("\n{0,25}", address[i]);

        if ( m->Success )
        {
            Console::Write("   User='{0}'",
            m->Groups["user"]->Value);
            Console::Write("   Host='{0}'",
            m->Groups["host"]->Value);
        }
        else
            Console::Write("   (invalid email address)");
        }

    Console::WriteLine("");
    return 0;
}
```

## <a name="regex_rearrange"></a> Réorganiser des données à l’aide d’Expressions régulières

L’exemple de code suivant montre comment la prise en charge des expressions régulières .NET Framework peut être utilisé pour les réorganiser ou reformater les données. Le code suivant exemple utilise le <xref:System.Text.RegularExpressions.Regex> et <xref:System.Text.RegularExpressions.Match> classes pour extraire les prénoms et noms d’une chaîne et afficher ces éléments dans l’ordre inverse.

Le <xref:System.Text.RegularExpressions.Regex> classe est utilisée pour construire une expression régulière qui décrit le format actuel des données. Les deux noms sont supposés être séparés par une virgule et peuvent utiliser n’importe quel volume de l’espace blanc autour de la virgule. Le <xref:System.Text.RegularExpressions.Match> méthode est ensuite utilisée pour analyser chaque chaîne. En cas de réussite, les prénoms et noms sont récupérés à partir de la <xref:System.Text.RegularExpressions.Match> de l’objet et l’affiche.

### <a name="example"></a>Exemple

```cpp
// regex_reorder.cpp
// compile with: /clr
#using <System.dll>
using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ name =
   {
      "Abolrous, Sam",
      "Berg,Matt",
      "Berry , Jo",
      "www.contoso.com"
   };

   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");

   for ( int i=0; i < name->Length; i++ )
   {
      Console::Write( "{0,-20}", name[i] );
      Match^ m = reg->Match( name[i] );
      if ( m->Success )
      {
         String^ first = m->Groups["first"]->Value;
         String^ last = m->Groups["last"]->Value;
         Console::WriteLine("{0} {1}", first, last);
      }
      else
         Console::WriteLine("(invalid)");
   }
   return 0;
}
```

## <a name="regex_search"></a> Utiliser des Expressions régulières pour rechercher et remplacer

L’exemple de code suivant montre comment la classe d’expression régulière <xref:System.Text.RegularExpressions.Regex> peut être utilisé pour effectuer la recherche et remplacement. Cette opération est effectuée avec la <xref:System.Text.RegularExpressions.Regex.Replace%2A> (méthode). La version utilisée prend deux chaînes comme entrée : la chaîne à modifier et la chaîne à insérer à la place les sections (le cas échéant) qui correspondent au modèle donné à la <xref:System.Text.RegularExpressions.Regex> objet.

Ce code remplace tous les chiffres dans une chaîne par des traits de soulignement (_), puis remplace les avec une chaîne vide, en les supprimant réellement. Le même effet peut être accompli en une seule étape, mais deux étapes sont utilisées ici à des fins de démonstration.

### <a name="example"></a>Exemple

```cpp
// regex_replace.cpp
// compile with: /clr
#using <System.dll>
using namespace System::Text::RegularExpressions;
using namespace System;

int main()
{
   String^ before = "The q43uick bro254wn f0ox ju4mped";
   Console::WriteLine("original  : {0}", before);

   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");
   String^ after = digitRegex->Replace(before, "_");
   Console::WriteLine("1st regex : {0}", after);

   Regex^ underbarRegex = gcnew Regex("_");
   String^ after2 = underbarRegex->Replace(after, "");
   Console::WriteLine("2nd regex : {0}", after2);

   return 0;
}
```

## <a name="regex_validate"></a> Utiliser des Expressions régulières pour valider la mise en forme des données

L’exemple de code suivant illustre l’utilisation d’expressions régulières pour vérifier la mise en forme d’une chaîne. Dans l’exemple de code suivant, la chaîne doit contenir un numéro de téléphone valide. L’exemple de code suivant utilise la chaîne « \d{3}-\d{3}-\d{4}» pour indiquer que chaque champ représente un numéro de téléphone valide. « D » dans la chaîne indique un chiffre, et l’argument après chaque « d » indique le nombre de chiffres qui doivent être présents. Dans ce cas, le nombre est nécessaire pour être séparés par des tirets.

### <a name="example"></a>Exemple

```cpp
// regex_validate.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ number =
   {
      "123-456-7890",
      "444-234-22450",
      "690-203-6578",
      "146-893-232",
      "146-839-2322",
      "4007-295-1111",
      "407-295-1111",
      "407-2-5555",
   };

   String^ regStr = "^\\d{3}-\\d{3}-\\d{4}$";

   for ( int i = 0; i < number->Length; i++ )
   {
      Console::Write( "{0,14}", number[i] );

      if ( Regex::IsMatch( number[i], regStr ) )
         Console::WriteLine(" - valid");
      else
         Console::WriteLine(" - invalid");
   }
   return 0;
}
```

## <a name="related-sections"></a>Rubriques connexes

[.NET Framework (expressions régulières)](/dotnet/standard/base-types/regular-expressions)

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)