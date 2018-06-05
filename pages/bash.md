##bash
···awk 'NR==FNR{a[$1];next} ($1) in a' test_2.txt test_1.txt···
