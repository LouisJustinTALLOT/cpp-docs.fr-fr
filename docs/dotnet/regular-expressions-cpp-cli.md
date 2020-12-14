---
description: 'En savoir plus sur : expressions régulières (C++/CLI)'
title: Expressions régulières (C++/CLI)
ms.date: 11/04/2016
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
ms.openlocfilehash: 429a121ec7acad46437a344b089f5c6a1ce4243b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245809"
---
# <a name="regular-expressions-ccli"></a>Expressions régulières (C++/CLI)

Illustre diverses opérations de chaîne utilisant des classes d’expressions régulières dans le .NET Framework.

Les rubriques suivantes illustrent l’utilisation de l' <xref:System.Text.RegularExpressions> espace de noms .NET Framework (et dans le cas de la <xref:System.String.Split%2A?displayProperty=fullName> méthode) pour rechercher, analyser et modifier des chaînes.

## <a name="parse-strings-using-regular-expressions"></a><a name="parse_regex"></a> Analyser des chaînes à l’aide d’expressions régulières

L’exemple de code suivant illustre l’analyse de chaîne simple à l’aide <xref:System.Text.RegularExpressions.Regex> de la classe dans l' <xref:System.Text.RegularExpressions?displayProperty=fullName> espace de noms. Une chaîne contenant plusieurs types de délimiteurs de mots est construite. La chaîne est ensuite analysée à l’aide <xref:System.Text.RegularExpressions.Regex> de la classe conjointement avec la <xref:System.Text.RegularExpressions.Match> classe. Ensuite, chaque mot de la phrase s’affiche séparément.

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

## <a name="parse-strings-using-the-split-method"></a><a name="parse_split"></a> Analyser des chaînes à l’aide de la méthode Split

L’exemple de code suivant illustre l’utilisation de la <xref:System.String.Split%2A?displayProperty=fullName> méthode pour extraire chaque mot d’une chaîne. Une chaîne contenant plusieurs types de délimiteurs de mots est construite, puis analysée en appelant <xref:System.String.Split%2A> avec une liste de délimiteurs. Ensuite, chaque mot de la phrase s’affiche séparément.

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

## <a name="use-regular-expressions-for-simple-matching"></a><a name="regex_simple"></a> Utiliser des expressions régulières pour une correspondance simple

L’exemple de code suivant utilise des expressions régulières pour rechercher des correspondances de sous-chaînes exactes. La recherche est effectuée par la <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> méthode statique, qui prend deux chaînes comme entrée. La première est la chaîne à rechercher et la seconde est le modèle à rechercher.

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

## <a name="use-regular-expressions-to-extract-data-fields"></a><a name="regex_extract"></a> Utiliser des expressions régulières pour extraire des champs de données

L’exemple de code suivant illustre l’utilisation d’expressions régulières pour extraire des données d’une chaîne mise en forme. L’exemple de code suivant utilise la <xref:System.Text.RegularExpressions.Regex> classe pour spécifier un modèle qui correspond à une adresse de messagerie. Ce guide comprend des identificateurs de champ qui peuvent être utilisés pour récupérer les portions d’utilisateur et de nom d’hôte de chaque adresse de messagerie. La <xref:System.Text.RegularExpressions.Match> classe est utilisée pour effectuer les critères spéciaux réels. Si l’adresse de messagerie spécifiée est valide, le nom d’utilisateur et les noms d’hôte sont extraits et affichés.

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

## <a name="use-regular-expressions-to-rearrange-data"></a><a name="regex_rearrange"></a> Utiliser des expressions régulières pour réorganiser des données

L’exemple de code suivant montre comment la prise en charge des expressions régulières .NET Framework peut être utilisée pour réorganiser ou reformater les données. L’exemple de code suivant utilise <xref:System.Text.RegularExpressions.Regex> les <xref:System.Text.RegularExpressions.Match> classes et pour extraire le prénom et le nom d’une chaîne, puis afficher ces éléments de nom dans l’ordre inverse.

La <xref:System.Text.RegularExpressions.Regex> classe est utilisée pour construire une expression régulière qui décrit le format actuel des données. Les deux noms sont supposés être séparés par une virgule et peuvent utiliser n’importe quelle quantité d’espace blanc autour de la virgule. La <xref:System.Text.RegularExpressions.Match> méthode est ensuite utilisée pour analyser chaque chaîne. En cas de réussite, le prénom et le nom sont récupérés à partir de l' <xref:System.Text.RegularExpressions.Match> objet et affichés.

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

## <a name="use-regular-expressions-to-search-and-replace"></a><a name="regex_search"></a> Utiliser des expressions régulières pour rechercher et remplacer

L’exemple de code suivant montre comment la classe d’expressions régulières <xref:System.Text.RegularExpressions.Regex> peut être utilisée pour effectuer des recherches et des remplacements. Cette opération s’effectue à l’aide de la <xref:System.Text.RegularExpressions.Regex.Replace%2A> méthode. La version utilisée prend deux chaînes comme entrée : la chaîne à modifier et la chaîne à insérer à la place des sections (le cas échéant) qui correspondent au modèle donné à l' <xref:System.Text.RegularExpressions.Regex> objet.

Ce code remplace tous les chiffres d’une chaîne par des traits de soulignement (_), puis les remplace par une chaîne vide, en les supprimant efficacement. Le même effet peut être accompli en une seule étape, mais deux étapes sont utilisées ici à des fins de démonstration.

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

## <a name="use-regular-expressions-to-validate-data-formatting"></a><a name="regex_validate"></a> Utiliser des expressions régulières pour valider la mise en forme des données

L’exemple de code suivant illustre l’utilisation d’expressions régulières pour vérifier la mise en forme d’une chaîne. Dans l’exemple de code suivant, la chaîne doit contenir un numéro de téléphone valide. L’exemple de code suivant utilise la chaîne « \d {3} -\d {3} -\d {4} » pour indiquer que chaque champ représente un numéro de téléphone valide. La chaîne « d » indique un chiffre et l’argument après chaque « d » indique le nombre de chiffres qui doivent être présents. Dans ce cas, le nombre doit être séparé par des tirets.

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

## <a name="related-sections"></a>Sections connexes

[Expressions régulières du .NET Framework](/dotnet/standard/base-types/regular-expressions)

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
