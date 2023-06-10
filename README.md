cat http_logs.log https_logs.log > merged_logs.log
awk '{split($4, date, "T"); split($7, filename, "/"); print date[1], "-", filename[length(filename)]}' merged_logs.log | sort > sorted_logs.txt
grep 'http://' sorted_logs.txt > http_log_summary.txt
grep 'https://' sorted_logs.txt > https_log_summary.txt
