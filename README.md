# Frequency-Sort

Given a string, sort it in decreasing order based on the frequency of characters.

<a href="https://ibb.co/nzBcvL7"><img src="https://i.ibb.co/r436Swx/frequency.jpg" alt="frequency" border="0"></a>

```csharp

public static string FrequencySort(string s)
        {
            char[] chars = s.ToCharArray();
            Dictionary<char, int> frequencyByChar = new Dictionary<char, int>();

            for (int i = 0; i < chars.Length; i++) {
                int count = 0;
                for (int j = 0; j < chars.Length; j++){
                    if (chars[i] == chars[j])
                        count++;
                }

                if (!frequencyByChar.Keys.Contains(chars[i]))
                    frequencyByChar.Add(chars[i], count);
            }

            var list = frequencyByChar.OrderByDescending(p => p.Value);
            string newString= string.Empty;

            foreach (var karakter in list){
                for (int i = 0; i < karakter.Value; i++)
                    newString = newString + karakter.Key;

                if (karakter.Value == 0)
                    newString = newString + karakter.Key;
            }

            return newString;
        }
