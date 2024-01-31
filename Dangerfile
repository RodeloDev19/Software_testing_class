# Dangerfile

# Rule: Check commit title length
warn("Commit title should be 50 characters or fewer") if git.commits.first&.message&.lines&.first&.chomp&.size.to_i > 50

# Rule: Check for an empty line between commit title and description
warn("There should be an empty line between the commit title and description") unless git.commits.first&.message&.lines&.second&.strip.to_s.empty?

# Rule: Check description length
warn("Commit description should have at least 5 characters") if git.commits.first&.message&.lines&.drop(2)&.join.size.to_i < 5

# Rule: Check each line in the description for length
git.commits.first&.message&.lines&.drop(2)&.each_with_index do |line, index|
  warn("Line #{index + 3} in the description should not exceed 72 characters") if line.chomp.size.to_i > 72
end
