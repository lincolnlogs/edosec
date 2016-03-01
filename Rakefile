POST_PATH = "_posts/"

desc "Create a new post for the second Wednesday of next month"
task :post do
	t = Time.now
	next_event = second_wednesday_of_next_month(t)

	filename = t.strftime("%Y-%m-%d-") + next_event.strftime("%B") + ".textile"

	data = ""
	data << "---\n"
	data << "layout: post\n"
	data << "title: " + next_event.strftime("%B %Y") + " EdoSec\n"
	data << "event-summary: EdoSec\n"
	data << "event-timezone: Japan/Tokyo\n"
	data << "event-start: " + next_event.strftime("%Y%m%d") + "T190000\n"
	data << "event-end: " + next_event.strftime("%Y%m%d") + "T220000\n"
	data << "event-location: Shibuya Hobgoblin\n"
	data << "---\n"
	data << "\n"
	data << "h1. " + next_event.strftime("%B %-d, %Y")
	data << "\n\n"
	data << "EdoSec will be at Shibuya Hobgoblin and starts at 7pm."
	data << " 江戸secは19時よりホブゴブリン渋谷にて開催します。"
	data << "\n"

	File.open(POST_PATH + filename, 'w') {|f| f.write(data) }
end

task :default => :post


def second_wednesday_of_next_month(t)
  if t.day < 8 and t.wday == 4
    t
  else
    second_wednesday_of_next_month(t + (60 * 60 * 24))
  end
end
